<script setup>
import { ref } from "vue"
const seleccionados = ref([])
const options = ["Elemento 1", "Elemento 2", "Elemento 3", "Elemento 4", "Elemento 5"]

const mostrarSeleccionados = () => {
    console.log("Elementos seleccionados:", seleccionados.value)
}
</script>
<template>
    <div class="flex flex-col justify-center items-center gap-5 mt-32">
        <select v-model="seleccionados" multiple class="border p-2 h-32">
            <option v-for="(op, index) in options" :key="index" :value="op">{{ op }}</option>      
        </select>
        <button class="bg-blue-500 p-1 cursor-pointer rounded hover:bg-blue-700 transition" @click="mostrarSeleccionados">Mostrar seleccionados</button>
        <h2 class="text-red-500">Seleccionados: {{ seleccionados.join(', ') }}</h2>
    </div>
</template>