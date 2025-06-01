<template>
    <!-- EJERCICIO 3 -->

    <div class="mt-5 pt-5">
        <h2 class="pb-5"> José Ivan - Ejercicio 3: Lista de tareas</h2>
        <ul class="list-unstyled">
            <li v-for="(tarea, index) in listaTareas" :key="index" class="row p-3 border">
                <h4 v-if="tarea.completada" class="m-0 p-1 col-10 text-decoration-line-through">{{ tarea.texto }}</h4>
                <h4 v-else class="m-0 p-1 col-10">{{ tarea.texto }}</h4>
                <button v-if="tarea.completada" class="col-2 btn btn-danger" @click="cambiarEstadoTarea(index)">{{
                    tarea.completada ? 'Finalizada' : 'Pendiente' }}</button>
                <button v-else class="col-2 btn btn-success" @click="cambiarEstadoTarea(index)">{{ tarea.completada ?
                    'Finalizada' : 'Pendiente' }}</button>
            </li>
        </ul>
    </div>
</template>

<script setup>

import { ref } from 'vue'
import { listaTareas } from '../tareas'



function cambiarEstadoTarea(index) {
    listaTareas.value[index].completada = !listaTareas.value[index].completada
}



</script>

<!-- <style scoped>
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
</style> -->