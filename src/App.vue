<template>
  <div id="app">
    <Calculadora />
  </div>
</template>

<script>
import Calculadora from './components/Calculadora.vue';

export default {
  name: 'App',
  components: {
    Calculadora
  }
};
</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
  margin-top: 20px;
}
</style>
