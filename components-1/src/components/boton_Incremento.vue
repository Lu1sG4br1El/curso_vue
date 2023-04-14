<script setup>
import {ref} from "vue"

const contadorI = ref(0)

const incrementar = () => contadorI.value++
</script>

<template>
    <button @click="incrementar">Incrementa aqui {{ contadorI }}</button>
</template>