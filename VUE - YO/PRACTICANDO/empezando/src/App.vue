<template>

<div class="principal row p-2 justify-content-center">
  <!-- Ejercicio 2 -->
    <Marcador/>

  <!-- Ejercicio 3 -->
    <Tareas/>

  <!-- Ejercicio 4 -->
    <Servicios/>

</div>

</template>

<script setup>
  import { ref } from 'vue'
  import Marcador from './components/marcador.vue'
  import Tareas from './components/Tareas.vue'
  import Servicios from './components/Servicios.vue'
</script>






<!-- scoped: los estilos solo afectan a este componente -->
<style>
  .principal {
      background-color: #ffffff;
      padding: 20px;
      /* border: 1px solid #ccc; */
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0);
      height: 100vh;
      margin-left: 50px;
      margin-right: 50px;
  }
  .secundario {
      text-align: center;
      border-radius: 10px;
      padding: 20px;
  }
</style>