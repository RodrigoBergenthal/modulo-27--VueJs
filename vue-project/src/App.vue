<script setup>
import { reactive } from "vue";
const nome = "rodrigo"
const meuOBJ = {
  nome: "gian",
  filmeFavorito: "Rocky"
}

function dizOla(nome) {
  return `${nome} diz oi`;
}

const enderecoDaImagemDoBatman = 'https://images.hdqwalls.com/wallpapers/batman-concept-art-classic-suit-a3.jpg';
const botaoEstaDesabilitado = false

//let contador = 0

const estado = reactive({
  contador: 0,
})

function incrementar () {
  estado.contador++;
}

function decrementar () {
  estado.contador --;
}
</script>

<template>
 <h1> {{ dizOla (nome)}}</h1>
 <img :src="enderecoDaImagemDoBatman" alt="">
 <button :disabled="botaoEstaDesabilitado"> Enviar mensagem</button>

 <br/>
 <hr/>

{{ estado.contador }}

<button @click='incrementar' type="button"> + </button>
<button @click="decrementar" type="button"> - </button>
</template>

<style scoped>
img {
  max-width: 200px;
}
</style>
