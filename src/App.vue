<script setup>
// Javascript 
import Header from './components/Header.vue'
import Calc from './components/Calc.vue'
</script>

<template>
  <!-- Html -->
  <div class="container">
    <Header></Header>
    <Calc></Calc>
  </div>
</template>

<style scoped>
/* Css */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  display: block;
  width: 640px;
  max-width: 100%;
  height: 800px;
  background-color: #0431f8;
  margin: 0 auto;
  border-radius: 15px;
  padding: 20px;
  margin-top: 25px;
}
</style>