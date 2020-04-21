<template>
  <div id="app">
    <Todos text_top="My to-dos"/>
  </div>
</template>

<script>
import Todos from './components/MyTodos.vue'

export default {
  name: 'app',
  components: {
    Todos
  }
}
</script>

<style>
body {
  margin: 0;
}
#app {
  font-family: -apple-system,BlinkMacSystemFont,"Segoe UI",
  Roboto,"Helvetica Neue",Arial,"Noto Sans",sans-serif,
  "Apple Color Emoji","Segoe UI Emoji","Segoe UI Symbol","Noto Color Emoji";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
