<!-- <template>
    
    <div class="secundario bg-white shadow">
        <h1>{{ equipo }}</h1>
        <h1 class="p-2 text-danger">{{ contador }}</h1>
        <button class="btn btn-success" @click="masuno">+1</button>
        <button class="btn btn-success" @click="masdos">+2</button>
        <button class="btn btn-success" @click="mastres">+3</button>
    </div>
</template>


<script setup>
    import { ref } from 'vue'
    const contador = ref(0)

    function masuno() {
        contador.value++
    }
    function masdos() {
        contador.value = contador.value + 2
    }
    function mastres() {
        contador.value = contador.value + 3
    }

    const props = defineProps({
        equipo: String
    })


</script>


scoped: los estilos solo afectan a este componente
<style scoped>
.secundario {
    text-align: center;
    border-radius: 10px;
    padding: 20px;
}
</style> -->

<template>
    <h1 class="text-center mt-5 mb-5">Marcador de Baloncesto</h1>

    <div class="col-4 w-25">
        <!-- <MarcadorEquipo :equipo="varEquipoLocal"></MarcadorEquipo> -->
        <div class="secundario bg-white shadow">
            <h1>Local</h1>
            <h1 class="p-2 text-danger">{{ contadorLocal }}</h1>
            <button class="btn btn-success" @click="masunoL">+1</button>
            <button class="btn btn-success" @click="masdosL">+2</button>
            <button class="btn btn-success" @click="mastresL">+3</button>
        </div>
    </div>

    <div class="col-4 text-center">
        <img :src="imgPelota" alt="" width=200>
        <div class="mt-5">
            <button class="btn btn-secondary mx-2" @click="resetear">Resetear</button>
            <button class="btn btn-primary mx-2" :disabled="esVisible" @click="agregarResultados">Terminar Partido</button>
            <button v-if="esVisible" class="btn btn-success" :disable="!esVisible" @click="habilitarBoton">Nuevo Juego</button>
            <button v-else class="btn btn-success" :class="enable">Nuevo Juego</button>
        </div>
    </div>

    <!-- Equipo Visitante -->
    <div class="col-4 w-25">
        <!-- <MarcadorEquipo :equipo="varEquipoVisitante"></MarcadorEquipo> -->
        <div class="secundario bg-white shadow">
            <h1>Visitante</h1>
            <h1 class="p-2 text-danger">{{ contadorVisitante }}</h1>
            <button class="btn btn-success" @click="masunoV">+1</button>
            <button class="btn btn-success" @click="masdosV">+2</button>
            <button class="btn btn-success" @click="mastresV">+3</button>
        </div>
    </div>

    <div v-if="indicador">
        <h2 class="mb-4">Resultados Finales</h2>
        <ul class="list-unstyled">
            <li v-for="(resu, index) in resultados" :key="index">
                <h4 class="border border-1 m-0 p-1">Resultado final: Local {{ resu.local }} - {{ resu.visitante }}
                    Visitante
                </h4>
            </li>
        </ul>

    </div>
</template>

<script setup>

    import { ref } from 'vue'
    const imgPelota = ref('../public/basketball.png')

    const contadorLocal = ref(0)
    const contadorVisitante = ref(0)
    const resultados = ref([])
    const indicador = ref(false)
    const esVisible = ref(false)


    // Contador Local
    function masunoL() {
        contadorLocal.value++
    }
    function masdosL() {
        contadorLocal.value = contadorLocal.value + 2
    }
    function mastresL() {
        contadorLocal.value = contadorLocal.value + 3
    }

    // Contador Visitante
    function masunoV() {
        contadorVisitante.value++
    }
    function masdosV() {
        contadorVisitante.value = contadorVisitante.value + 2
    }
    function mastresV() {
        contadorVisitante.value = contadorVisitante.value + 3
    }


    // Resetear contadores
    function resetear() {
        contadorLocal.value = 0
        contadorVisitante.value = 0
    }

    function habilitarBoton(){
        if (esVisible.value == false){
            esVisible.value=true
        }else{
            esVisible.value=false
        }   
        
    }

    function agregarResultados() {
        if (contadorLocal.value + contadorVisitante.value != 0) {
            indicador.value = true
            const nuevoResult = {
                local: contadorLocal.value,
                visitante: contadorVisitante.value
            };
            habilitarBoton()
            resultados.value.push(nuevoResult)
            resetear()
        } else {
            alert("No hay puntos para agregar")
        }
        
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