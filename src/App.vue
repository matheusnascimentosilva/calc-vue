<template>
  <div id="app">
    <Calculator />
  </div>
</template>

<script>
// Importe o componente Calculator
import ModuleCalc from '@/components/ModuleCalc.vue';

export default {
  name: 'App',
  components: {
    // Registre o componente para poder usá-lo
    Calculator: ModuleCalc
  }
}
</script>

<style>
/* Adicione seu estilo global aqui, se necessário */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
