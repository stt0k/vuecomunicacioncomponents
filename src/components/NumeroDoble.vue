<script setup>
import { watch } from 'vue';
import { useRoute, useRouter } from "vue-router"

const route = useRoute()
const router = useRouter()
let numero = route.params.numero ? parseInt(route.params.numero) : 0

    watch(
        () => route.params.numero,
        (newNum) => {
            numero = newNum ? parseInt(newNum) : 0
        }
    )

</script>
<template>
    <div class="container mx-auto mt-32">
        <h1>Número doble</h1>
        <h2>Parametro recibido: <span class="text-blue-500">{{ numero }}</span></h2>
        <h2>El numero doble es: <span class="text-green-500">{{ numero * 2 }}</span></h2>
        <button v-on:click="router.go(-1)" class="mb-2 cursor-pointer bg-blue-500 rounded p-1">Volver</button>
        <br>
        <button v-on:click="router.push('/numeros')" class="cursor-pointer bg-blue-500 rounded p-1">Ir a números</button>
    </div>
</template>