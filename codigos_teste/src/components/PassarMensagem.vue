<template>
  <mensagem title="Utilizando props" />
  <mensagem title="em componentes diferentes" />
  <mensagem title="com valores diferentes" />
</template>

<script>
  import mensagem from './Mensagem.vue'
  
  export default {
    name: "PassarMensagem",
    components: {
      mensagem
    },
    data() {
      return {}
    }
  }
</script>

<style>
</style>