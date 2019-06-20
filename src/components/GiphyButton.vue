<template lang="pug">
  .giphy
    button(v-if="!imageSrc" v-on:click="loadGif") {{buttonMessage}}
    p(v-if="loading && !hasError") {{loadingMessage}}
    p(v-if="hasError") {{errorMessage}}
    img(v-if="imageSrc && !loading" v-on:click="loadGif" v-bind:src="imageSrc")
</template>
<script>
import axios from 'axios'

export default {
  name: "GiphyButton",
  data: function(){
    return {
      buttonMessage: 'I\'m the button, F*ck you!',
      loadingMessage: "It's loading Brenda !",
      errorMessage: "Fuck ! Something went wrong Brenda !",
      hasError: false,
      loading: false,
      imageSrc: null,
      limitation: 20
    }
  },
  methods: {
    loadGif: function(){
      this.loading = true
      this.hasError = false
      axios.get(`http://api.giphy.com/v1/gifs/search?q=ron+swanson&api_key=PDVuWMOgqRfwEXMP2JaojKoIQuRpbRuq&limit=${this.limitation}`, {timeout: 5000})
      .then((data) => {
        this.loading = false
        let index = Math.floor(Math.random() * Math.floor(this.limitation))
        this.imageSrc = data.data.data[index].images.fixed_height.url
      })
      .catch((err) => {
        this.hasError = true
      })
    }
  }
}
</script>
