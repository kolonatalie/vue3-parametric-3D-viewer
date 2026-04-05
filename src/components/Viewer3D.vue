<script setup lang="ts">
import { SceneManager } from '@/core/SceneManager';
import { onMounted, ref, watch, onUnmounted, nextTick } from 'vue';


const props = defineProps<{
  params: { width: number; height: number; depth: number; color: string }
}>();

const canvasRef = ref<HTMLDivElement | null>(null);
let sceneManager: SceneManager | null = null;

onMounted(async () => {
  await nextTick();
  if (canvasRef.value) {
    sceneManager = new SceneManager(canvasRef.value, props.params);
    window.addEventListener('resize', onWindowResize);
  }
});

const onWindowResize = () => {
  if (canvasRef.value && sceneManager) {
    sceneManager.onResize(canvasRef.value.clientWidth, canvasRef.value.clientHeight);
  }
};

watch(() => props.params, (newParams) => {
  sceneManager?.updateParams(newParams);
}, { deep: true });

onUnmounted(() => {
  window.removeEventListener('resize', onWindowResize);
  sceneManager?.dispose();
});
</script>

<template>
  <div ref="canvasRef" class="viewer"></div>
</template>
