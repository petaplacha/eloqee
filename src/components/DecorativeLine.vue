<script setup lang="ts">
import { computed } from 'vue'

type Point = { x: number; y: number }
type BezierSegment = { c1: Point; c2: Point; end: Point }

const props = withDefaults(defineProps<{
  start?: Point
  segments?: BezierSegment[]
  color?: 'magenta' | 'green' | 'purple' | string
  strokeWidth?: string
  viewBox?: string
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
})

const palette = {
  magenta: 'var(--color-brand-magenta)',
  green: 'var(--color-brand-green)',
  purple: 'var(--color-brand-purple)',
} as const

const pathData = computed(() => {
  const commands = [`M ${props.start.x} ${props.start.y}`]

  for (const segment of props.segments) {
    commands.push(
      `C ${segment.c1.x} ${segment.c1.y} ${segment.c2.x} ${segment.c2.y} ${segment.end.x} ${segment.end.y}`,
    )
  }

  return commands.join(' ')
})

const strokeColor = computed(() => palette[props.color as keyof typeof palette] ?? props.color)
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
      :d="pathData"
      :stroke="strokeColor"
      :stroke-width="strokeWidth"
      vector-effect="non-scaling-stroke"
      stroke-linecap="round"
      stroke-linejoin="round"
    />
  </svg>
</template>