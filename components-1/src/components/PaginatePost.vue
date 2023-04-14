<script setup>
defineProps(['inicio','fin'])

const emit = defineEmits(["next", "prev"])
</script>

<template>
    <div class="btn-group" role="group" aria-label="Basic example">
        <button @click="emit('prev')" :disabled="inicio <= 0" type="button" class="btn btn-outline-primary">Anterior {{ inicio }}</button>
        <button @click="emit('next')" :disabled="fin >= 100" type="button" class="btn btn-outline-primary">Siguiente {{ fin }}</button>
      </div>
</template>