<template>
    <div class="card m-2 p-2">
        <h5>{{ nombre }}</h5>
        <p>{{ correo }}</p>
    </div>
</template>

<script setup>
defineProps({
    nombre: String,
    correo: String
})
</script>
