<template>
  <div id="app">
      <Todos />
  </div>
</template>

<script>
import Todos from './components/Todos.vue'

export default {
  name: 'App',
  components: {
    Todos
  }
}
</script>

<style>
html {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
