<script setup>
import axios from 'axios';
import { ref } from 'vue';
import { useRoute,useRouter } from 'vue-router';


const route = useRoute();
const router = useRouter();
const poke = ref({});

const atras = () => {
    router.push('/pokemons')
}

const getData = async () => {
    try{
        const {data} = await axios.get(
            'https://pokeapi.co/api/v2/pokemon/${route.params.name}'
        );
        console.log(data);
        poke.value=data;
    }catch(error){
        console.log(error);
    }
};
getData();
</script>
<template>
    <img :src="poke.sprites.front_default">
    <div>
        <h2>Nombre del pokemon: {{ $route.params.name }}</h2>
        <button @click="atras">Atras</button>
    </div>
</template>