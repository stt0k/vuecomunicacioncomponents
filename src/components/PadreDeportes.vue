<script setup>
import HijoDeporte from './HijoDeporte.vue';
import { ref } from "vue"

const deportes = ref(["Curling", "Rugby", "Futbol", "Baloncesto"])
</script>
<template>
    <div class="flex flex-col justify-center items-center mt-32">
        <h1 class="text-blue-500">Padre deportes</h1>
        <ul>
            <li v-for="sport in deportes" :key="sport">
                <HijoDeporte :nombredeporte="sport" />
            </li>
        </ul>
    </div>
</template>