<script setup>
// defineProps(['id', 'titulo', 'contenido'])
defineprops({
    titulo : String, 
    id : Number,
    contenido : {
        type : String, 
        default : 'Sin descripción'
    }

})
</script>




<template>
<div class="card">
    <div class="card-body">
        <h5 class="card-title">{{id}} - {{titulo}}</h5>
        <p>{{ contenido }}</p>
    </div>
</div>

<BlogPost :id=1 titulo="Primer Post" contenido="Contenido del primer post"></BlogPost>
  <BlogPost :id=2 titulo="Segundo Post" contenido="Contenido del segundo post"></BlogPost>
  <BlogPost :id=3 titulo="tercer Post" contenido="Contenido del tercer post"></BlogPost>
  <BlogPost :id=4 titulo="Cuarto Post"></BlogPost>
</template>





<style>


</style>