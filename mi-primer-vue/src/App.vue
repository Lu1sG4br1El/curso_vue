<template>
  <div class="conteiner text-center">
    <h1>Hola {{ name.toUpperCase() }}</h1>
    <br>
    <h2 style="color: red">Gabo</h2>
    <br>
    <ul>
      <template v-for="item in array_Objetos" :key="item.nombre">
          <li v-if="item.stock > 0">{{ item.nombre }} - {{ item.precio }} - {{ item.descripcion }}</li>
      </template>
    </ul>


    <br>


    <h2 style="color: aqua;">Lista de usuarios</h2>
    <br>
    <ul class="list-group">
      <template v-for="(usuario, index) in Usuarios" :key="usuario.id">
        <li class="list-group-item list-group-item-dark">
          <h3>{{ usuario.nombre }}</h3>
          <ul>
            <template v-for="(post, index) in usuario.posts" :key="post.id">
              <li>{{ post.title }}</li>
            </template>
          </ul>
        </li>
      </template>
    </ul>


    <br>
    

    <h2 style="color: silver;">Interaccion con el usuario final
    <br>
    <button type="button" class="btn btn-info" v-on:click.right.prevent="Evento_Click('Hiciste click :v')">right</button>
    <button type="button" class="btn btn-info" @click="Evento_Click('Hiciste click aqui tambien :3')">left</button>
    <button type="button" class="btn btn-info" @click.middle="Evento_Click('Otra vez hiciste click >:|')">middle</button>
    </h2>
    <br>
    <h3 style="color: springgreen;">Contador</h3>
    <br>
    <h4 :class="contadorComputed">{{ contar }}
      <br>
      <button type="button" class="btn btn-success" @click="incrementar">Aumentar</button>
      <button type="button" class="btn btn-danger" @click="decrementar">Disminuir</button>
      <button type="button" class="btn btn-warning" @click="resetear">Resetear</button>
      <button type="button" class="btn btn-primary" @click="clasAdd" :disabled="bloqueoSimilar">Add</button>
      <br>
      {{ array_NumerosFav }}
      <ul class="list-group">
        <li class="list-group-item list-group-item-dark" v-for="numeros,index in array_NumerosFav" :key="index">
          {{ numeros }}
        </li>
      </ul>
    </h4>
    <br>
  </div>
</template>



<script setup>

import {ref,computed} from 'vue'

const name = 'este es mi vue dinamico';
const array_Objetos = [
  {
    nombre: "laptop",
    precio: "$15.000",
    descripcion: "Una laptop",
    stock: 20
  },
  {
    nombre: "telefono",
    precio: "$7.000",
    descripcion: "Android",
    stock: 10
  },
  {
    nombre: "reloj",
    precio: "$5.000",
    descripcion: "Reloj inteligente",
    stock: 10
  }];
const Usuarios = [
  {
    id: 1,
    name: 'Luis',
    posts: [
      {id: 1, title: 'Mi 1er post'},
      {id: 2, title: 'Mi 2do post'}
    ]
  },
  {
    id: 1,
    name: 'Gabriel',
    posts: [
      {id: 1, title: 'Mi 3er post'},
      {id: 2, title: 'Mi 4to post'}
    ]
  }
]
const Evento_Click = (message) => {
  console.log(message)
}

const contar = ref(0)

const contadorComputed = computed(() => {
  if(contar.value > 0){
    return "positivo"
  }
  if(contar.value < 0){
    return "negativo"
  }
  if(contar.value === 0){
    return "neutro"
  }
})

const array_NumerosFav = ref([])

const clasAdd = () => {
  array_NumerosFav.value.push(contar.value)
}

const bloqueoSimilar = computed(() => {
  const numSearch = array_NumerosFav.value.find((numeros) => numeros === contar.value)
  console.log(numSearch)
  if(numSearch === 0) return true
  return numSearch ? true : false
})

const incrementar = () => contar.value++
const decrementar = () => contar.value--
const resetear = () => (contar.value = 0)

</script>



<style>
h1{
  color: white;
}
body{
  background-color: aqua;
}
h4{
  color: red;
}
.positivo{
  color: green;
}
.negativo{
  color: red;
}
.neutro{
  color: white;
}
</style>