<script setup>
import { reactive } from '@vue/reactivity'
import Layout from './components/Layout.vue'
import LayoutSettings from './components/LayoutSettings.vue'

const dynamicLayout = reactive({
  gridTemplateAreas: '"header header header" "aside main main" "aside footer footer"',
})

const layoutChanged = (payload) => {
  if (payload.asidePosition === 'right' && payload.headerPosition === 'top') {
    dynamicLayout.gridTemplateAreas =
      '"header header header" "main main aside" "footer footer aside"'
  } else if (payload.asidePosition === 'left' && payload.headerPosition === 'top') {
    dynamicLayout.gridTemplateAreas =
      '"header header header" "aside main main" "aside footer footer"'
  } else if (payload.asidePosition === 'right' && payload.headerPosition === 'bottom') {
    dynamicLayout.gridTemplateAreas =
      '"main main aside" "footer footer aside" "header header header"'
  } else if (payload.asidePosition === 'left' && payload.headerPosition === 'bottom') {
    dynamicLayout.gridTemplateAreas =
      '"aside main main" "aside footer footer" "header header header"'
  }
}
</script>

<template>
  <Layout :dynamicLayout="dynamicLayout">
    <LayoutSettings @changed="layoutChanged" />
  </Layout>
</template>
