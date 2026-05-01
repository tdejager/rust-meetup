<script setup lang="ts">
const props = withDefaults(
  defineProps<{
    side?: 'left' | 'right'
    sideOffset?: string
    top?: string
    width?: string
    rotate?: number
    fontSize?: string
    cornerSize?: number
  }>(),
  {
    side: 'right',
    sideOffset: '6%',
    top: '14%',
    width: '50%',
    rotate: 2,
    fontSize: '0.62rem',
    cornerSize: 16,
  },
)

// The visible folded corner sits on the inner side of the card —
// opposite to where the card is anchored to the slide.
const cornerSide = props.side === 'right' ? 'left' : 'right'
const cardRotate = props.side === 'right' ? props.rotate : -props.rotate
</script>

<template>
  <div
    class="recipe-card"
    :class="[`recipe-card--corner-${cornerSide}`]"
    :style="{
      [side]: props.sideOffset,
      top,
      width,
      transform: `rotate(${cardRotate}deg)`,
      fontSize,
      '--corner-size': `${cornerSize}px`,
    }"
  >
    <slot />
  </div>
</template>

<style scoped>
.recipe-card {
  position: absolute;
  background: var(--tufte-bg);
  border: 1px solid var(--tufte-rule);
  border-radius: 3px;
  padding: 0.4rem 0.9rem;
  box-shadow:
    0 6px 18px rgba(0, 0, 0, 0.18),
    0 1px 3px rgba(0, 0, 0, 0.12);
  z-index: 20;
}
/* Notch the corner out of the card itself so the triangle below shows
 * through cleanly — gives a real folded-paper silhouette. */
.recipe-card--corner-right {
  clip-path: polygon(
    0 0,
    calc(100% - var(--corner-size)) 0,
    100% var(--corner-size),
    100% 100%,
    0 100%
  );
}
.recipe-card--corner-left {
  clip-path: polygon(
    var(--corner-size) 0,
    100% 0,
    100% 100%,
    0 100%,
    0 var(--corner-size)
  );
}

/* The triangle in the notch — the back of the folded-up corner. */
.recipe-card::before {
  content: '';
  position: absolute;
  top: 0;
  width: 0;
  height: 0;
  border-style: solid;
  /* slight tonal shift so the fold reads as a different surface */
  --fold-tone: rgba(0, 0, 0, 0.08);
  filter: drop-shadow(0 1px 0.5px rgba(0, 0, 0, 0.12));
}
.recipe-card--corner-right::before {
  right: 0;
  /* right-angle at top-right; hypotenuse runs from (-cs, 0) to (0, cs) */
  border-width: 0 var(--corner-size) var(--corner-size) 0;
  border-color: transparent var(--fold-tone) transparent transparent;
}
.recipe-card--corner-left::before {
  left: 0;
  /* mirrored: right-angle at top-left */
  border-width: var(--corner-size) var(--corner-size) 0 0;
  border-color: var(--fold-tone) transparent transparent transparent;
}

.recipe-card :deep(pre),
.recipe-card :deep(code),
.recipe-card :deep(.shiki),
.recipe-card :deep(.slidev-code) {
  max-height: none !important;
  overflow: visible !important;
  white-space: pre !important;
  line-height: 1.25 !important;
  background: transparent !important;
  border: none !important;
  padding: 0 !important;
  margin: 0 !important;
}
</style>
