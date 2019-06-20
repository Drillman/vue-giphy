<template lang="pug">
  #app
    GiphyButton
</template>


<script>
import GiphyButton from './components/GiphyButton'

export default {
  name: 'app',
  components: {
    GiphyButton
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
