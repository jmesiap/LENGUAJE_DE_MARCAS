<!-- <template>
    <div class="card h-100 shadow-sm">
        <img :src="imagen" class="card-img-top" alt="Imagen del artista" />
        <div class="card-body">
            <h5 class="card-title">{{ nombre }}</h5>
            <p class="card-text">{{ genero }}</p>
        </div>
    </div>
</template>

<script setup>
defineProps({
    nombre: String,
    genero: String,
    imagen: String
})
</script>

<style scoped>
.card-img-top {
    object-fit: cover;
    height: 200px;
}


</style> -->

<!-- desde una api -->

<template>
  <div class="card h-100 shadow-sm">
    <img :src="imagen || defaultImage" class="card-img-top" alt="Imagen del artista" />
    <div class="card-body">
      <h5 class="card-title">{{ nombre }}</h5>
      <p class="card-text">{{ genero || 'Género no disponible' }}</p>
      <p class="card-text"><small class="text-muted">{{ pais || 'País desconocido' }}</small></p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  nombre: String,
  genero: String,
  pais: String,
  imagen: String
})

const defaultImage = 'https://via.placeholder.com/300x200?text=No+Image'
</script>

<style scoped>
.card-img-top {
  object-fit: cover;
  height: 200px;
}
</style>


