<template>
  <div>
    <p>{{count}}</p>
    <contador @contar="count++" /><br><br><br><br><br><br>
    <contador2 />
  </div>
</template>

<script>
import contador from './Contador.vue'
import contador2 from './Contador2.vue'

export default {
  name: 'AcionarContador',
  components: {
    contador,
    contador2
  },
  data() {
    return {
      count: 0
    }
  }
}
</script>

<style>
</style>