<!-- App.vue -->
<template>
  <h1 class="text-center">{{ mensaje }}</h1>
  <p class="text-center">{{ parrafo }}</p>
  <hr>
  <!-- *********************************************************************************************** -->

  <p>1. Crea una lista con v-for que muestre 5 lenguajes de programación.</p>
  <p>2. Usa v-if para mostrar un mensaje si la lista está vacía.</p>
  <p v-if="lenguajesDeProgramacion.length === 0">Lista Vacia</p>
  <ul v-else>
    <li v-for="(leng, i) in lenguajesDeProgramacion" :key="i">
      {{ leng }}
    </li>
  </ul>

  <p>3. Crea un formulario con v-model que permita escribir el nombre de un alumno y mostrarlo en tiempo real.</p>
  <input v-model="nombreAlumno" placeholder="Escribe tu nombre" size="100" />
  <p>{{ nombreAlumno }}</p>

  <p>4. Usa un botón con @click para limpiar el campo de texto anterior.</p>
  <button @click='limpiarFormulario'>Limpiar</button>
  <hr>


  <!-- ****************************** CONTADOR ***************************************************************** -->

  <div class="pt-5 text-center">
    <p>1. Crea un botón que incremente un contador.</p>
    <p>2. Crea un botón que lo reinicie a 0.</p>
    <p>3. Muestra el valor triple del contador usando computed.</p>

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






  <hr>
  <!-- *********************************************************************************************** -->


  <div class="mt-5 text-center">

    <p>4. Crea un input que actualice un mensaje, y muestra también la cantidad de caracteres escritos.</p>
    <input @input="contarCaracteres" />
    <p class="mt-5">Mensaje: {{ mensajeContar }}</p>
    <p>Cantidad de caracteres: {{ caracteres }}</p>
  </div>


  <hr>
  <!-- *********************************************************************************************** -->

  <div class="container mt-5">
    <h1 class="text-primary">Formulario de contacto - version con v-model</h1>
    <input class="form-control mb-3" v-model="nombre" placeholder="Tu nombre" />
    <button class="btn btn-success" @click="saludar">Saludar</button>

    <div v-if="nombre" class="alert alert-info mt-3">
      ¡Hola {{ nombre }}!
    </div>
  </div>
  <hr>
  <!-- *********************************************************************************************** -->

  <div class="container mt-5">
    <h1 class="text-info">Formulario de contacto - verasion con evento (sin v-model)</h1>
    <input @input="activarSaludo" placeholder="Ingresa tu nombre" class="form-control mb-5">
    <i v-if="nombreSinVBind" class="bi bi-emoji-smile">¡ Hola, {{ nombreSinVBind }} !</i>
  </div>


  <hr>
  <!-- *********************************************************************************************** -->

  <div class="container">
    <div class="row">
      <div class="col-md-6">
        <p>Columna izquierda</p>
      </div>
      <div class="col-md-6">
        <p>Columna derecha</p>
      </div>
    </div>
  </div>

</template>


<!-- **************************************************************************************************** -->
<!-- **************************************************************************************************** -->
<!-- **************************************************************************************************** -->
<!-- **************************************************************************************************** -->


<script setup>
import { ref, computed } from 'vue'

// *********************************************************************************************************
const mensaje = ref('¡Bienvenido al curso Vue 3!')
const parrafo = ref('José Ivan Mesia Portocarrero')
const lenguajesDeProgramacion = ref(["Java", "Kotlin", "JavaScript", "Python", "C#"])
const nombreAlumno = ref('')
const caracteres = ref(0)
const mensajeContar = ref('')
const arrayFavoritos = ref([])

function limpiarFormulario() {
  nombreAlumno.value = ''
}
// ************************************ CONTADOR *********************************************************************
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

// *********************************************************************************************************
function contarCaracteres(e) {
  mensajeContar.value = e.target.value
  caracteres.value = e.target.value.length
}

// *********************************************************************************************************
const nombre = ref('')

function saludar() {
  // no hace falta nada, solo mostrar el mensaje reactivo
}

// *********************************************************************************************************

const nombreSinVBind = ref('')
function activarSaludo(e) {
  nombreSinVBind.value = e.target.value
}

const anadir=()=>{
  arrayFavoritos.value.push( contador.value );
}
const bloquearBoton = computed(()=>{
  if (arrayFavoritos.value.find((num)=> num === contador.value)) return true
  if (contador.value === 0) return false
  return false
  //return numero palo palo numero == 0
  
  })
</script>
