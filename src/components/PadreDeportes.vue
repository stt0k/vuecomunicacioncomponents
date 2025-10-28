<script setup>
import HijoDeporte from './HijoDeporte.vue';
import { ref } from "vue"

const deportes = ref(["Curling", "Rugby", "Futbol", "Baloncesto"])
var favorito = ref(null)

const seleccionarFavoritoParent = (deporteFavorito) => {
    console.log("Yo soy tu padre")
    favorito.value = deporteFavorito
}

</script>
<template>
    <div class="flex flex-col justify-center items-center mt-32">
        <h1 class="text-blue-500 text-2xl font-bold">Padre deportes</h1>
        <h2 class="bg-yellow-500" v-if="favorito">
            Su deporte favorito es {{ favorito }}
        </h2>
        <ul>
            <li v-for="sport in deportes" :key="sport">
                <HijoDeporte v-on:seleccionarFavoritoParent="seleccionarFavoritoParent" :nombredeporte="sport" />
            </li>
        </ul>
    </div>
</template>