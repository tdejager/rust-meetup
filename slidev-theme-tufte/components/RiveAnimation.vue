<script setup lang="ts">
import { onBeforeUnmount, onMounted, ref } from 'vue'
import { Rive } from '@rive-app/canvas-lite'

const props = withDefaults(
  defineProps<{
    src: string
    stateMachine?: string
    artboard?: string
    autoplay?: boolean
  }>(),
  {
    stateMachine: 'State Machine 1',
    autoplay: true,
  },
)

const canvas = ref<HTMLCanvasElement | null>(null)
let rive: Rive | null = null

onMounted(() => {
  if (!canvas.value) return
  rive = new Rive({
    src: props.src,
    canvas: canvas.value,
    autoplay: props.autoplay,
    stateMachines: props.stateMachine,
    artboard: props.artboard,
    onLoad: () => rive?.resizeDrawingSurfaceToCanvas(),
  })
})

onBeforeUnmount(() => {
  rive?.cleanup()
  rive = null
})
</script>

<template>
  <div class="rive-animation">
    <canvas ref="canvas" />
  </div>
</template>

<style scoped>
.rive-animation {
  width: 100%;
  height: 100%;
}
.rive-animation canvas {
  width: 100%;
  height: 100%;
  display: block;
}
</style>
