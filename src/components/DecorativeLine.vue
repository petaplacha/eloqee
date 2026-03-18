<script setup lang="ts">
import { computed, nextTick, onMounted, ref, watch } from 'vue'

type Point = { x: number; y: number }
type BezierSegment = { c1: Point; c2: Point; end: Point }
type DrawDirection = 'forward' | 'reverse'

const props = withDefaults(defineProps<{
  start?: Point
  segments?: BezierSegment[]
  color?: 'magenta' | 'green' | 'purple' | string
  strokeWidth?: string
  viewBox?: string
  drawDuration?: number
  drawDelay?: number
  drawDirection?: DrawDirection
}>(), {
  start: () => ({ x: 0, y: -240 }),
  segments: () => ([
    { c1: { x: 2, y: -8 }, c2: { x: 8, y: 10 }, end: { x: 18, y: 28 } },
    { c1: { x: 30, y: 48 }, c2: { x: 56, y: 42 }, end: { x: 60, y: 66 } },
    { c1: { x: 64, y: 92 }, c2: { x: 34, y: 102 }, end: { x: 42, y: 126 } },
    { c1: { x: 50, y: 148 }, c2: { x: 92, y: 146 }, end: { x: 102, y: 164 } },
    { c1: { x: 118, y: 184 }, c2: { x: 80, y: 196 }, end: { x: 94, y: 214 } },
    { c1: { x: 116, y: 228 }, c2: { x: 170, y: 212 }, end: { x: 224, y: 236 } },
  ]),
  color: 'magenta',
  strokeWidth: 'var(--decorative-line-stroke-width, 3.75em)',
  viewBox: '0 -24 210 260',
  drawDuration: 0,
  drawDelay: 0,
  drawDirection: 'forward',
})

const palette = {
  magenta: 'var(--color-brand-magenta)',
  green: 'var(--color-brand-green)',
  purple: 'var(--color-brand-purple)',
} as const

const pathRef = ref<SVGPathElement | null>(null)
const drawAnimationRef = ref<SVGAnimateElement | null>(null)
const drawLength = ref<number | null>(null)

const reversedSegments = computed<BezierSegment[]>(() => {
  const segments: BezierSegment[] = []

  for (let index = props.segments.length - 1; index >= 0; index -= 1) {
    const segment = props.segments[index]
    const previousPoint = index === 0 ? props.start : props.segments[index - 1].end

    segments.push({
      c1: segment.c2,
      c2: segment.c1,
      end: previousPoint,
    })
  }

  return segments
})

const renderedStart = computed(() => {
  if (props.drawDirection === 'reverse' && props.segments.length > 0) {
    return props.segments[props.segments.length - 1].end
  }

  return props.start
})

const renderedSegments = computed(() => (
  props.drawDirection === 'reverse' ? reversedSegments.value : props.segments
))

const pathData = computed(() => {
  const commands = [`M ${renderedStart.value.x} ${renderedStart.value.y}`]

  for (const segment of renderedSegments.value) {
    commands.push(
      `C ${segment.c1.x} ${segment.c1.y} ${segment.c2.x} ${segment.c2.y} ${segment.end.x} ${segment.end.y}`,
    )
  }

  return commands.join(' ')
})

const strokeColor = computed(() => palette[props.color as keyof typeof palette] ?? props.color)
const shouldDraw = computed(() => props.drawDuration > 0 && drawLength.value !== null)
const dashLength = computed(() => (drawLength.value === null ? undefined : String(drawLength.value)))

const syncDrawAnimation = async () => {
  await nextTick()

  const path = pathRef.value

  if (!path) return

  const totalLength = path.getTotalLength()

  if (!Number.isFinite(totalLength) || totalLength <= 0) {
    drawLength.value = null
    return
  }

  drawLength.value = totalLength

  if (props.drawDuration <= 0) return

  await nextTick()

  path.setAttribute('stroke-dasharray', String(totalLength))
  path.setAttribute('stroke-dashoffset', String(totalLength))
  drawAnimationRef.value?.beginElementAt(props.drawDelay)
}

onMounted(() => {
  void syncDrawAnimation()
})

watch([
  pathData,
  () => props.drawDuration,
  () => props.drawDelay,
  () => props.drawDirection,
], () => {
  void syncDrawAnimation()
})
</script>

<template>
  <svg
    :viewBox="viewBox"
    fill="none"
    xmlns="http://www.w3.org/2000/svg"
    aria-hidden="true"
    class="pointer-events-none overflow-visible"
  >
    <path
      ref="pathRef"
      :d="pathData"
      :stroke="strokeColor"
      :stroke-width="strokeWidth"
      :stroke-dasharray="shouldDraw ? dashLength : undefined"
      :stroke-dashoffset="shouldDraw ? dashLength : undefined"
      vector-effect="non-scaling-stroke"
      stroke-linecap="round"
      stroke-linejoin="round"
    >
      <animate
        v-if="shouldDraw"
        ref="drawAnimationRef"
        attributeName="stroke-dashoffset"
        :from="dashLength"
        to="0"
        :dur="`${props.drawDuration}s`"
        begin="indefinite"
        calcMode="linear"
        fill="freeze"
      />
    </path>
  </svg>
</template>
