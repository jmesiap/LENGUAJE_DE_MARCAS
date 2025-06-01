<template>


  <div class="shadows mt-5 container row p-0">
    <h1 class="mt-4">Ejercicio 4: Componentes</h1>
    <h1 class="mt-4">Nuestros Servicios</h1>
    <!-- <div class="row"> -->
      <div v-for="(serv, index) in servicios" :key='index' class="card border shadow mt-5 col-3 p-2 me-0 text-center">
        <img :src="serv.imagen_url" alt="Imagen del servicio" class="" />
        <div class="card-body">
          <h5 class="card-title">{{ serv.titulo }}</h5>
          <p v-if="!serv.descripcion || serv.descripcion.length === 0" class="card-text">Sin descripción</p>
          <p v-else>{{ serv.descripcion }}</p>
          <button v-if="'texto_boton' in serv" class="btn btn-primary">
            {{ serv.texto_boton }} 
          </button>
          <button v-else class="btn btn-primary">Contratar</button>
        </div>
      </div>
    </div>
  <!-- </div> -->


</template>

<script setup>
import { ref } from 'vue'
import { servicios } from '../servicios'

</script>

<!-- <style>
</style> -->