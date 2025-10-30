<script setup>
import { onMounted, ref } from "vue"

const numeros = ref([])

const generarRandoms = () => {
    numeros.value = []
    for (let i = 0; i < 2; i++) {
        const randNum = Math.floor(Math.random() * 100) + 1
        numeros.value.push(randNum)
    }
}

onMounted(() => {
    generarRandoms()
    console.log(numeros.value)
})

</script>
<template>
    <li v-for="num in numeros" :key="num">
        <router-link class="hover:text-white/60 transition" :to="`/tablamultiplicar/${num}`">Tabla {{ num }}</router-link>
    </li>
</template>