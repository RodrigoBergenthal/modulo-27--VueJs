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
  email:"",
  saldo: 5000,
  transferindo: 0,

})

function incrementar () {
  estado.contador++;
}

function decrementar () {
  estado.contador --;
}

function alteraEmail (evento){
 estado.email = evento.target.value;
}

function mostraSaldoFuturo (){
  const {saldo , transferindo} = estado;
  return saldo - transferindo;
}

function validaValorTransferencia (){
  const {saldo , transferindo} = estado;
  return saldo >= transferindo;
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
<br/>
<hr/>

{{ estado.email }}
<input type="email" @keyup="alteraEmail">
<br/>
<hr/>

Saldo: {{ estado.saldo }}<br/>
Transferindo: {{ estado.transferindo }}<br/>
Saldo depois da Transferência: {{ mostraSaldoFuturo () }}<br/>
<input :class="{invalido: !validaValorTransferencia()}" @keyup="evento => estado.transferindo = evento.target.value" type="number" placeholder="Quantia para transferir" />

</template>

<style scoped>
img {
  max-width: 200px;
}

.invalido {
  outline-color:red ;
  border-color: red;
}
</style>
