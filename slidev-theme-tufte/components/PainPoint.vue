<script setup lang="ts">
withDefaults(
  defineProps<{
    color?: string
    strokeWidth?: number
    /** Higher = more hand-drawn jitter on the ellipse strokes. */
    wobble?: number
  }>(),
  {
    color: '#c14a26',
    strokeWidth: 1.4,
    wobble: 1.6,
  },
)

// Random id so multiple instances on a slide don't collide.
const filterId = `pp-wobble-${Math.random().toString(36).slice(2, 9)}`
</script>

<template>
  <span class="pain-point">
    <svg
      class="pain-point__circle"
      viewBox="0 0 200 100"
      preserveAspectRatio="none"
      aria-hidden="true"
    >
      <defs>
        <!-- Turbulence + displacement adds a hand-drawn jitter to the
             two paths' strokes without changing their nominal size. -->
        <filter
          :id="filterId"
          x="-5%"
          y="-15%"
          width="110%"
          height="130%"
        >
          <feTurbulence
            type="fractalNoise"
            baseFrequency="0.05"
            numOctaves="2"
            seed="3"
          />
          <feDisplacementMap in="SourceGraphic" :scale="wobble" />
        </filter>
      </defs>
      <g :filter="`url(#${filterId})`">
        <!-- Hand-crafted ellipse paths with intentional slight asymmetry
             so the underlying shape already feels drawn rather than
             machined; the turbulence filter then jitters the strokes. -->
        <path
          d="
            M 8 52
            C 7 24, 36 5, 96 4
            C 162 3, 195 22, 194 50
            C 195 78, 161 96, 99 96
            C 35 97, 8 79, 8 52
            Z"
          fill="none"
          :stroke="color"
          :stroke-width="strokeWidth"
          stroke-linecap="round"
          vector-effect="non-scaling-stroke"
        />
        <path
          d="
            M 11 49
            C 10 26, 38 8, 100 7
            C 160 6, 192 25, 192 51
            C 191 76, 158 93, 96 93
            C 36 94, 12 75, 11 49
            Z"
          fill="none"
          :stroke="color"
          :stroke-width="strokeWidth * 0.7"
          stroke-linecap="round"
          opacity="0.55"
          vector-effect="non-scaling-stroke"
        />
      </g>
    </svg>
    <span class="pain-point__text"><slot /></span>
  </span>
</template>

<style scoped>
.pain-point {
  position: relative;
  display: inline-block;
  /* Padding controls how far the circle sits beyond the text. */
  padding: 1.6em 2.4em;
  margin: 0.4em 0;
}
.pain-point__text {
  position: relative;
  z-index: 1;
  font-family: var(--tufte-serif);
  font-weight: 700;
  font-size: 1.15rem;
  line-height: 1.3;
  color: var(--tufte-text);
  display: inline-block;
  max-width: 28ch;
  text-wrap: balance;
}
.pain-point__circle {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
  pointer-events: none;
  overflow: visible;
}
</style>
