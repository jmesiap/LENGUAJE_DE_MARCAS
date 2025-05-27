<script setup>
import { ref } from 'vue'
import BlogPost from './components/BlogPost.vue'
const arrayPost = ref({[
  { id: 1, titulo: "Post 01", contenido: "Descripción del post 01"},
  { id: 2, titulo: "Post 01", contenido: "Descripción del post 01"},
  { id: 3, titulo: "Post 01", contenido: "Descripción del post 01"},
  { id: 4, titulo: "Post 01", },
]});

</script>
<template>
  <div class="container">
    <h1>Componentes</h1>
    <br>
    <div>
      </div>
  
  </div>
</template>


<style>

</style>