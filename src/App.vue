<template>
  <div id="app">
    <code>{{psdJson}}</code>
    <div id="ImageContainer"></div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      psdJson: null
    }
  },
  mounted () {
    this.parsePSD()
  },
  methods: {
    parsePSD () {
      let PSD = require('psd.js')
      PSD.fromURL('/pad-demo.psd').then((psd) => {
        this.psdJson = psd.tree().export()
        console.log(psd.tree().export())
        document.getElementById('ImageContainer').appendChild(psd.image.toPng());
      })
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
