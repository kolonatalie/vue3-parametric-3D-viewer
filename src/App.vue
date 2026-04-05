<script setup lang="ts">
import { reactive, ref } from 'vue';
import Viewer3D from './components/Viewer3D.vue';
import Controls from './components/Controls.vue';
import type { BoxParams } from './core/types';

const STORAGE_KEY = 'v3d_params';
const isOrdered = ref(false);

const DEFAULT_PARAMS: BoxParams = {
  width: 1,
  height: 1,
  depth: 1,
  color: '#2c3e50'
};

const saved = localStorage.getItem(STORAGE_KEY);
const boxParams = reactive<BoxParams>(saved ? JSON.parse(saved) : { ...DEFAULT_PARAMS });

const updateParams = (newParams: BoxParams) => {
  Object.assign(boxParams, newParams);
  localStorage.setItem(STORAGE_KEY, JSON.stringify(boxParams));
};

const resetConfig = () => {
  updateParams(DEFAULT_PARAMS);
  isOrdered.value = false;
};

const handleOrder = (data: BoxParams) => {
  console.log('Sending to production...', data);
  isOrdered.value = true;
};
</script>

<template>
  <div class="app-container">
    <Viewer3D :params="boxParams" class="main-viewer" />
    <Controls :params="boxParams" @update:params="updateParams" @submit="handleOrder" />

    <Transition name="fade">
      <div v-if="isOrdered" class="order-overlay" @click="isOrdered = false">
        <div class="order-card" @click.stop>
          <h2>Order Confirmed</h2>

          <div class="order-summary">
            <div class="summary-item"><span>Width:</span> <strong>{{ boxParams.width }}m</strong></div>
            <div class="summary-item"><span>Height:</span> <strong>{{ boxParams.height }}m</strong></div>
            <div class="summary-item"><span>Depth:</span> <strong>{{ boxParams.depth }}m</strong></div>
            <div class="summary-item">
              <span>Color:</span>
              <div class="color-preview" :style="{ backgroundColor: boxParams.color }"></div>
            </div>
          </div>

          <div class="order-card__actions">
            <button class="btn-secondary" @click="isOrdered = false">Close</button>
            <button class="btn-primary" @click="resetConfig">Start Again</button>
          </div>
        </div>
      </div>
    </Transition>
  </div>
</template>
