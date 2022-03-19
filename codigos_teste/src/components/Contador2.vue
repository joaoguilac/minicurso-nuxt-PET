<template>
  <button @click="count++">Clicou {{count}} vezes</button>
</template>

<script>
export default {
  name: 'contador2',
  data() {
    return {
      count: 0
    }
  }
}
</script>

<style>
</style>