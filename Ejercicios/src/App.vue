<!-- /******************************** SCRIPT *******************************************/ -->

<script setup>
import { ref, computed, onMounted } from 'vue'

// Usando un boton mostrar el contenido de un input text

const mostrar = ref(false)
const hola = ref(' ')
const nombre = ref(' ')
const exclama = ref(' ')

function saludar() {

  if (txt_nombre.value.trim() == '') {
    mostrar.value = false
    hola.value = ''
    nombre.value = ''
    exclama.value = ''
  } else {
    mostrar.value = true
    hola.value = "Hola,"
    nombre.value = txt_nombre.value
    exclama.value = "!!!"
  }
}

// Reflejar el contenido de un input text en un h3, usando v-model
const apellido = ref('')
function verificaVacio() {
  if (txt_nombre.value.trim() == '') {
    mostrar.value = false
  }
}

// Mostrar y ocultar parrafo
const mostrarParrafo = ref(true)


// Listar productos usando v-for
const productos = ['Azucar', 'Arroz', 'Sal', 'Queso', 'Leche']


// CONTADOR
const contador = ref(0)

function incrementarContador() {
  contador.value++
}
const tripleContador = computed(() => contador.value * 3)

function reiniciarContador() {
  contador.value = 0
}

function DisminuirContador() {
  contador.value--
}
const arrayFavoritos = ref([])
const anadir = () => {
  arrayFavoritos.value.push(contador.value);
}
const bloquearBoton = computed(() => {
  if (arrayFavoritos.value.find((num) => num === contador.value)) return true
  if (contador.value === 0) return false
  return false
  //return numero palo palo numero == 0

})




// Componentes


import Encabezado from './components/Encabezado.vue'
import Boton from './components/Boton.vue'
import PieDePagina from './components/PieDePagina.vue'


// ejemplo de cards, componentes y props
import Card from './components/Card.vue'

// mas ejemplos
import Usuario from './components/Usuario.vue'

const usuarios = [
  { nombre: 'Ana Pérez', correo: 'ana@example.com' },
  { nombre: 'Carlos García', correo: 'carlos@example.com' },
  { nombre: 'Luisa Torres', correo: 'luisa@example.com' }
]

// Mostrando artistas
// import ArtistaCard from './components/ArtistaCard.vue'
// const artistasAPI = [
//   { id: 1, nombre: 'Rosalía', genero: 'Flamenco pop', imagen: 'https://via.placeholder.com/300x200?text=Rosalía' },
//   { id: 2, nombre: 'Bad Bunny', genero: 'Reggaeton', imagen: 'https://via.placeholder.com/300x200?text=Bad+Bunny' },
//   { id: 3, nombre: 'Adele', genero: 'Soul / Pop', imagen: 'https://via.placeholder.com/300x200?text=Adele' },
//   { id: 4, nombre: 'BTS', genero: 'K-pop', imagen: 'https://via.placeholder.com/300x200?text=BTS' },
//   { id: 5, nombre: 'Coldplay', genero: 'Rock alternativo', imagen: 'https://via.placeholder.com/300x200?text=Coldplay' }
// ]

// const artistas = ref([])
// const criterio = ref('nombre')

// onMounted(() => {
//   // Simula una llamada a una API
//   artistas.value = artistasAPI
// })

// const artistasOrdenados = computed(() => {
//   return [...artistas.value].sort((a, b) => {
//     return a[criterio.value].localeCompare(b[criterio.value])
//   })
// })



// desde una api

import ArtistaCard from './components/ArtistaCard.vue'

const artistas = ref([])

onMounted(async () => {
  const idsArtistas = ['111239', '135988', '111279'] // Coldplay, Adele, Metallica
  const resultados = []

  for (let id = 112000; id <= 112052; id++) {
    try {
      const response = await fetch(`https://www.theaudiodb.com/api/v1/json/2/artist.php?i=${id}`)
      const data = await response.json()
      if (data.artists && data.artists[0]) {
        resultados.push(data.artists[0])
      }
    } catch (error) {
      console.error(`Error al obtener datos del ID ${id}:`, error)
    }
  }

  artistas.value = resultados
})

</script>

/****************************** TEMPLATE *******************************************/

<template>
  <!-- Usando un boton mostrar el contenido de un input text -->
  <div class="shadow border border-2 p-5 mb-5">
    <h3 v-if="mostrar">{{ hola }} {{ nombre }} {{ exclama }}</h3>
    <h3 v-else-if="!mostrar">Ingrese un Nombre</h3>
    <input id="txt_nombre" @input="verificaVacio" placeholder="Escribe tu nombre" />
    <button class="m-5 btn btn-primary" @click="saludar">Saludar</button>
  </div>

  <!-- Reflejar el contenido de un input text en un h3, usando v-model -->
  <div class="shadow border border-2 p-5 mb-5">
    <h3>{{ apellido }}</h3>
    <input class="mt-5" v-model="apellido" placeholder="Ingrese su nombre" />

  </div>


  <!-- Mostrar y ocultar parrafo -->
  <div class="shadow border border-2 p-5 mb-5">
    <p v-if="mostrarParrafo">Valor a Mostrar u ocultar</p>
    <button class="btn btn-success" @click="mostrarParrafo = !mostrarParrafo">
      {{ mostrarParrafo ? "Ocultar" : "Mostrar" }}
    </button>
  </div>


  <!-- Muestra una lista de productos usando v-for. -->

  <div class="shadow border border-2 p-5 mb-5">
    <h3>Productos</h3>
    <ul class="mt-5 list-unstyled text-start">
      <li v-for="(prod, i) in productos" :key="i">
        {{ i + 1 }} {{ prod }}

      </li>
    </ul>
  </div>


  <div class="shadow border border-2  p-5 text-center">
    <div class="container bg-body">Contador
      <p v-if="contador < 0" class="text-danger">{{ contador }}</p>
      <p v-else-if="contador > 0" class="text-success">{{ contador }}</p>
      <p v-else class="text-primary">{{ contador }}</p>

    </div>

    <div>Contador Triple
      <p class="text-success">{{ tripleContador }}</p>
    </div>

    <button class="mx-2" @click="DisminuirContador">Disminuir</button>
    <button class="mx-2" @click="reiniciarContador">Reiniciar</button>
    <button class="mx-2" @click="incrementarContador">Incrementar</button>
    <button class="mx-2" @click="anadir()" :disabled="bloquearBoton">Añadir Array</button>
    {{ arrayFavoritos }}
  </div>


  <!-- columnas con bootstrap -->
  <div class=" shadow mt-5 p-5 container">
    <div class="row">
      <div class="col-md-6">
        <p>Columna izquierda</p>
      </div>
      <div class="col-md-6">
        <p>Columna derecha</p>
      </div>
    </div>
  </div>


  <!-- Componentes -->
  <div class="shadow border border-2 mt-5 p-5">
    <Encabezado />
    <Boton />
    <PieDePagina />
  </div>

  <!-- ejemplo de cards, componentes y props -->

  <div class="shadows border border-2 mt-5 p-5 container">
    <h1 class="mt-4">Ejemplo de Props con Cards</h1>
    <div class="row">
      <Card titulo="Montaña nevada" texto="Una hermosa vista de las montañas."
        imagen="https://picsum.photos/id/1015/300/200" enlace="https://ejemplo.com/montana" />
      <Card titulo="Playa soleada" texto="Un día perfecto para nadar." imagen="https://picsum.photos/id/1016/300/200"
        enlace="https://ejemplo.com/playa" />
      <Card titulo="Bosque verde" texto="Naturaleza pura y aire limpio." imagen="https://picsum.photos/id/1018/300/200"
        enlace="https://ejemplo.com/bosque" />
    </div>
  </div>

  <!-- mas ejemplos -->

  <h2>Lista de Usuarios</h2>
  <Usuario v-for="(usuario, index) in usuarios" :key="index" :nombre="usuario.nombre" :correo="usuario.correo" />

  <!-- Mostrando artistas -->

   <!-- <div class="container py-4">
    <h2 class="mb-4">🎶 Lista de Artistas</h2>

    <div class="mb-3">
      <label for="orden" class="form-label">Ordenar por:</label>
      <select v-model="criterio" class="form-select w-auto" id="orden">
        <option value="nombre">Nombre</option>
        <option value="genero">Género</option>
      </select>
    </div>

    <div class="row row-cols-1 row-cols-md-3 g-4">
      <div v-for="artista in artistasOrdenados" :key="artista.id" class="col">
        <ArtistaCard
          :nombre="artista.nombre"
          :genero="artista.genero"
          :imagen="artista.imagen"
        />
      </div>
    </div>
  </div> -->



<!-- desde una api-->

<div class="container py-4">
    <h2 class="mb-4 text-center">🎸 Artistas desde TheAudioDB por ID</h2>

    <div class="row row-cols-1 row-cols-md-3 g-4">
      <div v-for="artista in artistas" :key="artista.idArtist" class="col">
        <ArtistaCard
          :nombre="artista.strArtist"
          :imagen="artista.strArtistThumb"
          :genero="artista.strGenre"
          :pais="artista.strCountry"
        />
      </div>
    </div>
  </div>

</template>
/****************************** ESTILOS *******************************************/
<style></style>