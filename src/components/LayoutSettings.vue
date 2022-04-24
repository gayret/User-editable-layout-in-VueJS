<script setup>
import { reactive } from '@vue/reactivity'
import { watch } from '@vue/runtime-core'
import { defineEmits } from 'vue'

const emit = defineEmits(['layoutSettingsChanged'])

const state = reactive({
  layoutSettings: {
    asidePosition: 'left',
    headerPosition: 'top',
  },
})

watch(state.layoutSettings, () => {
  emit('changed', state.layoutSettings)
})
</script>

<template>
  <h1>Layout Settings</h1>
  <div class="user-selection">
    <div class="card">
      <strong>Aside Position</strong>
      <label>
        <input
          value="left"
          name="aside-position"
          v-model="state.layoutSettings.asidePosition"
          type="radio"
        />
        Left
      </label>
      <label>
        <input
          value="right"
          name="aside-position"
          v-model="state.layoutSettings.asidePosition"
          type="radio"
        />
        Right
      </label>
    </div>

    <div class="card">
      <strong>Header Position</strong>
      <label>
        <input
          value="top"
          name="header-position"
          v-model="state.layoutSettings.headerPosition"
          type="radio"
        />
        Top
      </label>
      <label>
        <input
          value="bottom"
          name="header-position"
          v-model="state.layoutSettings.headerPosition"
          type="radio"
        />
        Bottom
      </label>
    </div>
  </div>
</template>

<style scoped>
.user-selection {
  display: flex;
  gap: 1em;
}

.card {
  padding: 1em;
  border: 1px solid #ccc;
}

strong {
  display: block;
}
</style>
