<template>
    <button @click="saludar">Haz clic</button>
</template>

<script>
export default {
    name: 'Boton',
    methods: {
        saludar() {
            alert("¡Hola desde el componente Botón!");
        }
    }
}
</script>
