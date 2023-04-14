<!--Zona Script-->


<script setup>
import BlogPost from "./components/BlogPost.vue";
import boton_Incremento from "./components/boton_Incremento.vue"
import PaginatePost from "./components/PaginatePost.vue"
import {ref} from "vue"

const posts = ref([
    {title: 'post 1', id: 1, body: 'descripcion 1'},
    {title: 'post 2', id: 2, body: 'descripcion 2'},
    {title: 'post 3', id: 3}
])

const favorito = ref('')

const postXpagina = 10
const inicio = ref(0)
const fin = ref(postXpagina)

const cambiarFavorito = (title) => {
    favorito.value = title
}

fetch("https://jsonplaceholder.typicode.com/posts")
    .then((res) => res.json())
    .then((data) => {
        posts.value = data
    })

const siguiente = () => {
    inicio.value = inicio.value + postXpagina
    fin.value = fin.value + postXpagina
}

const anterior = () => {
    inicio.value = inicio.value - postXpagina
    fin.value = fin.value - postXpagina
}

</script>


<!--Zona Template-->

<template>
<div class="container">
    <h1>Nuevo proyecto</h1>
    <br>
    <h2 style="color: red;">Gabo</h2>
    <br>
    <PaginatePost @next="siguiente" @prev="anterior" :inicio="inicio" :fin="fin" class="mb-2"/>
    <br>
    <boton_Incremento></boton_Incremento>
    <br>
    <BlogPost
        v-for="post in posts.slice(inicio, fin)"
        :key="post.id"
        :title="post.title" 
        :id="post.id"
        :body="post.body"
        @PropiedadCF="cambiarFavorito"
        class="mb-2"
    ></BlogPost>
    <br>
    <h2 style="color: cyan;">Mi post favorito: {{ favorito }}</h2>
    
</div>
</template>