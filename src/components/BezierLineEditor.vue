<script setup lang="ts">
import { computed, onBeforeUnmount, onMounted, ref } from 'vue'
import DecorativeLine from './DecorativeLine.vue'

type Point = { x: number; y: number }
type BezierSegment = { c1: Point; c2: Point; end: Point }
type Side = 'left' | 'right' | 'top' | 'bottom'

const props = withDefaults(defineProps<{
  color?: 'magenta' | 'green' | 'purple' | string
  strokeWidth?: string
  margin?: number
}>(), {
  color: 'magenta',
  strokeWidth: '4em',
  margin: 96,
})

const rootRef = ref<HTMLElement | null>(null)
const isDrawingMode = ref(false)
const throughPoints = ref<Point[]>([])
const viewport = ref({ width: window.innerWidth, height: window.innerHeight })

const updateViewport = () => {
  viewport.value = { width: window.innerWidth, height: window.innerHeight }
}

const isTypingTarget = (target: EventTarget | null) => {
  return target instanceof HTMLInputElement
    || target instanceof HTMLTextAreaElement
    || (target instanceof HTMLElement && target.isContentEditable)
}

const handleKeydown = (event: KeyboardEvent) => {
  if (event.code === 'Space' && !isTypingTarget(event.target)) {
    event.preventDefault()
    isDrawingMode.value = !isDrawingMode.value
  }

  if (event.code === 'Escape') {
    throughPoints.value = []
    isDrawingMode.value = false
  }
}

const handleCanvasClick = (event: MouseEvent) => {
  if (!isDrawingMode.value || !rootRef.value) {
    return
  }

  const rect = rootRef.value.getBoundingClientRect()
  throughPoints.value = [
    ...throughPoints.value,
    { x: event.clientX - rect.left, y: event.clientY - rect.top },
  ]
}

const nearestSide = (point: Point, size: { width: number; height: number }): Side => {
  const distances = [
    { side: 'left' as const, value: point.x },
    { side: 'right' as const, value: size.width - point.x },
    { side: 'top' as const, value: point.y },
    { side: 'bottom' as const, value: size.height - point.y },
  ]

  return distances.sort((a, b) => a.value - b.value)[0].side
}

const extendPointToSide = (
  point: Point,
  direction: Point,
  side: Side,
  size: { width: number; height: number },
  margin: number,
): Point => {
  const epsilon = 0.001

  if (side === 'left') {
    if (Math.abs(direction.x) < epsilon) {
      return { x: -margin, y: point.y }
    }

    const t = (-margin - point.x) / direction.x
    return t > 0
      ? { x: -margin, y: point.y + direction.y * t }
      : { x: -margin, y: point.y }
  }

  if (side === 'right') {
    if (Math.abs(direction.x) < epsilon) {
      return { x: size.width + margin, y: point.y }
    }

    const t = (size.width + margin - point.x) / direction.x
    return t > 0
      ? { x: size.width + margin, y: point.y + direction.y * t }
      : { x: size.width + margin, y: point.y }
  }

  if (side === 'top') {
    if (Math.abs(direction.y) < epsilon) {
      return { x: point.x, y: -margin }
    }

    const t = (-margin - point.y) / direction.y
    return t > 0
      ? { x: point.x + direction.x * t, y: -margin }
      : { x: point.x, y: -margin }
  }

  if (Math.abs(direction.y) < epsilon) {
    return { x: point.x, y: size.height + margin }
  }

  const t = (size.height + margin - point.y) / direction.y
  return t > 0
    ? { x: point.x + direction.x * t, y: size.height + margin }
    : { x: point.x, y: size.height + margin }
}

const curvePoints = computed<Point[]>(() => {
  if (throughPoints.value.length < 2) {
    return throughPoints.value
  }

  const first = throughPoints.value[0]
  const second = throughPoints.value[1]
  const last = throughPoints.value[throughPoints.value.length - 1]
  const previous = throughPoints.value[throughPoints.value.length - 2]

  const startDirection = {
    x: first.x - second.x,
    y: first.y - second.y,
  }

  const endDirection = {
    x: last.x - previous.x,
    y: last.y - previous.y,
  }

  const startSide = nearestSide(first, viewport.value)
  const endSide = nearestSide(last, viewport.value)

  return [
    extendPointToSide(first, startDirection, startSide, viewport.value, props.margin),
    ...throughPoints.value,
    extendPointToSide(last, endDirection, endSide, viewport.value, props.margin),
  ]
})

const bezierSegments = computed<BezierSegment[]>(() => {
  if (curvePoints.value.length < 2) {
    return []
  }

  return curvePoints.value.slice(0, -1).map((point, index) => {
    const p0 = curvePoints.value[Math.max(0, index - 1)]
    const p1 = point
    const p2 = curvePoints.value[index + 1]
    const p3 = curvePoints.value[Math.min(curvePoints.value.length - 1, index + 2)]

    return {
      c1: {
        x: p1.x + (p2.x - p0.x) / 6,
        y: p1.y + (p2.y - p0.y) / 6,
      },
      c2: {
        x: p2.x - (p3.x - p1.x) / 6,
        y: p2.y - (p3.y - p1.y) / 6,
      },
      end: p2,
    }
  })
})

const curveStart = computed<Point | null>(() => curvePoints.value[0] ?? null)

const viewBox = computed(() => {
  const size = viewport.value
  return `${-props.margin} ${-props.margin} ${size.width + props.margin * 2} ${size.height + props.margin * 2}`
})

const generatedConfig = computed(() => {
  if (!curveStart.value || bezierSegments.value.length === 0) {
    return 'Klikni alespoň na 2 body.'
  }

  return JSON.stringify({
    start: curveStart.value,
    segments: bezierSegments.value,
    viewBox: viewBox.value,
  }, null, 2)
})

onMounted(() => {
  window.addEventListener('keydown', handleKeydown)
  window.addEventListener('resize', updateViewport)
})

onBeforeUnmount(() => {
  window.removeEventListener('keydown', handleKeydown)
  window.removeEventListener('resize', updateViewport)
})
</script>

<template>
  <div
    ref="rootRef"
    class="absolute inset-0"
    :class="isDrawingMode ? 'z-30 cursor-crosshair pointer-events-auto' : 'z-0 pointer-events-none'"
    @click="handleCanvasClick"
  >
    <DecorativeLine
      v-if="curveStart && bezierSegments.length > 0"
      :start="curveStart"
      :segments="bezierSegments"
      :view-box="viewBox"
      :color="color"
      :stroke-width="strokeWidth"
      class="absolute inset-0 h-full w-full opacity-90"
    />

    <div
      v-for="(point, index) in throughPoints"
      :key="`${point.x}-${point.y}-${index}`"
      class="absolute h-3 w-3 -translate-x-1/2 -translate-y-1/2 rounded-full border border-brand-white bg-brand-surface shadow-[0_0_0_2px_rgba(242,56,167,0.5)]"
      :style="{ left: `${point.x}px`, top: `${point.y}px` }"
    />
  </div>

  <aside class="pointer-events-none absolute bottom-4 left-4 z-20 max-w-[22rem] rounded-2xl border border-brand-white/12 bg-brand-black/45 p-4 text-xs text-brand-white/85 backdrop-blur-sm">
    <p class="font-semibold text-brand-white">Bezier line editor</p>
    <p class="mt-2">`Space` zapne/vypne kreslení. `Esc` smaže body.</p>
    <p class="mt-1">Průchozí body: {{ throughPoints.length }} · mód: {{ isDrawingMode ? 'DRAW' : 'OFF' }}</p>
    <pre class="mt-3 max-h-40 overflow-auto whitespace-pre-wrap text-[10px] leading-relaxed text-brand-white/70">{{ generatedConfig }}</pre>
  </aside>
</template>