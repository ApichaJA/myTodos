<template>
  <div class="My-to-dos">
    <h1>{{ text_top }}</h1>
    <input v-model="message" placeholder="edit me pls">
  </div>
</template>

<script>
  export default {
    name: 'Todos',
    props: {
      text_top: String,
    }
  }
</script>

<style>

</style>