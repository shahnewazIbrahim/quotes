<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <Quotes class="bg-gray-300"/>
</template>

<script>
import Quotes from './components/Quotes.vue'

export default {
  name: 'App',
  components: {
    Quotes
  },
  data() {
    return {
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
