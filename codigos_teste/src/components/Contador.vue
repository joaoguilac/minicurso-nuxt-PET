<template>
  <button @click="$emit('contar')">
    Aumentar contagem
  </button>
</template>

<script>
export default {
  name: 'contador',
  emits: ['contar'],
  data() {
    return {}
  }
}
</script>

<style>
</style>