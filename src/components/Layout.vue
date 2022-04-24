<script setup>
import { reactive } from '@vue/reactivity'

const props = defineProps({
  dynamicLayout: Object,
})
</script>

<template>
  <div class="layout" :style="[props.dynamicLayout]">
    <header>
      <h1>Header</h1>
    </header>
    <aside>
      <h2>Aside</h2>
    </aside>
    <main>
      <slot />
    </main>
    <footer>
      <h2>Footer</h2>
      <div>
        Follow me on <a href="https://safa.medium.com">Medium</a> and
        <a href="https://github.com/gayret/User-editable-layout-in-VueJS">Github</a>
      </div>
    </footer>
  </div>
</template>

<style scoped>
header {
  grid-area: header;
  background-color: lightsalmon;
}
aside {
  grid-area: aside;
  background-color: lightblue;
}
main {
  grid-area: main;
  background-color: lightcyan;
}
footer {
  grid-area: footer;
  background-color: lightyellow;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.layout {
  display: grid;
  grid-template-columns: auto 1fr;
}

.layout * {
  padding: 1em;
}
</style>
