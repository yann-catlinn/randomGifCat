<template>
  <div id="app">
    <random-gif-cat></random-gif-cat>
  </div>
</template>

<script>
import randomGifCat from './components/randomGifCat.vue'
  export default {
    data() {
      return {};
    },
    components: {
        'random-gif-cat':randomGifCat,
    }
  }
</script>

<style scoped>

</style>