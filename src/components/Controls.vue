<script setup lang="ts">
const props = defineProps<{
  params: { width: number; height: number; depth: number; color: string }
}>();
const emit = defineEmits(['update:params', 'submit']);

const availableColors = [
  { name: 'Anthracite', hex: '#2c3e50' },
  { name: 'Red', hex: '#e74c3c' },
  { name: 'Oak Wood', hex: '#d35400' },
  { name: 'White Gloss', hex: '#ecf0f1' },
  { name: 'Space Gray', hex: '#7f8c8d' }
];

const update = (key: string, value: string | number) => {
  emit('update:params', { ...props.params, [key]: value });
};

const handleOrder = () => {
  emit('submit', props.params);
};
</script>

<template>
  <div class="controls">
    <header class="controls__header">
      <h3>Model Configurator</h3>
      <p class="u-text-muted">Adjust dimensions and select materials.</p>
    </header>

    <div class="controls__params">
      <div class="controls__section">
        <h4>Dimensions</h4>

        <div v-for="dim in (['width', 'height', 'depth'] as const)" :key="dim" class="field">
          <div class="field__label-group">
            <label :for="`${dim}-number`">{{ dim.toUpperCase() }}</label>

            <input 
              :id="`${dim}-number`"
              type="number" 
              step="0.01" 
              :value="params[dim]" 
              aria-label="Enter exact value in meters"
              @input="e => update(dim, +(e.target as HTMLInputElement).value)" 
            />
            <p aria-hidden="true">m</p>
          </div>

          <input 
            type="range" 
            min="0.1" 
            max="4" 
            step="0.01" 
            :value="params[dim]"
            :aria-label="`Adjust ${dim} using slider`"
            @input="e => update(dim, +(e.target as HTMLInputElement).value)" 
          />
        </div>
      </div>

      <div class="controls__section">
        <h4>Material Color</h4>
        <div class="color-grid">
          <button v-for="color in availableColors" :key="color.hex" class="color-btn"
            :class="{ 'is-active': params.color === color.hex }" :style="{ backgroundColor: color.hex }"
            @click="update('color', color.hex)" :title="color.name">
          </button>
        </div>
      </div>
    </div>

    <div class="controls__footer">
      <div class="info-box">
        <span>Estimated Volume: </span>
        <strong>{{ (params.width * params.height * params.depth).toFixed(2) }} m³</strong>
      </div>
      <button class="btn-primary" @click="handleOrder">Order</button>
    </div>
  </div>
</template>
