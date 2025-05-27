<!-- Ejercicio 1 -->
<!-- Crea una aplicación simple en Vue donde el usuario pueda ingresar su nombre -->
<!-- y que este se muestre automáticamente en un saludo debajo del input. -->

<!-- /******************************** SCRIPT *******************************************/ -->

<script setup>
import { ref } from 'vue'
const mostrar = ref(false)
const hola = ref(' ')
const nombre = ref(' ')
const exclama = ref (' ')

const apellido = ref('')

function saludar() {

if (txt_nombre.value.trim() == ''){ 
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

function verificaVacio(){
  if (txt_nombre.value.trim() == ''){
    mostrar.value = false
    }

}
</script>

/****************************** TEMPLATE *******************************************/

<template>
  <h3 v-if="mostrar">{{ hola }} {{ nombre }} {{ exclama }}</h3>
  <h3 v-else-if="!mostrar">Ingrese un Nombre</h3>
  <input id="txt_nombre" @input="verificaVacio" placeholder="Escribe tu nombre"/>  
  <button class="m-5" @click="saludar">Saludar</button>
  
<hr>

  <h3>{{ apellido }}</h3>
  <input class="mt-5" v-model="apellido" placeholder="Ingrese su nombre"/>
</template>

<br>
<hr>


/****************************** ESTILOS *******************************************/
<style></style>