<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <PassarMensagem />
  <AcionarContador />
</template>

<script>
import PassarMensagem from './components/PassarMensagem.vue'
import AcionarContador from './components/AcionarContador.vue'

export default {
  name: 'App',
  components: {
    PassarMensagem,
    AcionarContador
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
