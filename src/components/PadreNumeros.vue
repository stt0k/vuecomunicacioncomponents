<script setup>
import { ref } from "vue"
import HijoNumero from './HijoNumero.vue';

const suma = ref(0)
const numeros = ref([])

const sumarNumero = (num) => {
    suma.value = suma.value + parseInt(num)
}

const generarNumerosAleatorio = () => {
    let random = parseInt(Math.random() * 50) + 1
    numeros.value.push(random)
}


</script>
<template>
    <div class="flex flex-col justify-center items-center mt-32">
        <h1 class="text-blue-500 text-2xl font-bold">Numeros Padre</h1>
        <h2 class="mb-5">La suma es: {{ suma }}</h2>
        <button class="bg-yellow-500 p-1 rounded cursor-pointer mb-5 hover:bg-yellow-800 transition" v-on:click="generarNumerosAleatorio">Nuevos Numero</button>
        <div class="flex flex-col justify-center items-center gap-5">
            <HijoNumero numero="14" v-on:sumarNumero="sumarNumero"/>
            <HijoNumero numero="22" v-on:sumarNumero="sumarNumero"/>
            <HijoNumero
                v-for="(num, i) in numeros"
                :key="i"
                :numero="num"
                v-on:sumar-numero="sumarNumero"
            />
        </div>
    </div>
</template>