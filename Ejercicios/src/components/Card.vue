<template>
    <div class="card m-3" style="width: 18rem;">
        <img :src="imagen" class="card-img-top" alt="Imagen de la tarjeta">
        <div class="card-body">
            <h5 class="card-title">{{ titulo }}</h5>
            <p class="card-text">{{ texto }}</p>
            <a :href="enlace" class="btn btn-primary">Ver más</a>
        </div>
    </div>


    
</template>

<script setup>
defineProps({
    titulo: String,
    texto: String,
    imagen: String,
    enlace: String
})
</script>
