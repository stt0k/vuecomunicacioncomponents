<script setup>
import { ref } from "vue"
import MenuTablaMultiplicar from "../MenuTablaMultiplicar.vue";

const numeros = ref([77,33])

</script>
<template>
    <div>
        <ul class="flex gap-2 mt-5 justify-end">
            <li>
                <router-link class="hover:text-white/60 transition" to="/">Deportes</router-link>
            </li>
            <li>
                <router-link class="hover:text-white/60 transition" to="/numeros">Números</router-link>
            </li>
            <li>
                <router-link class="hover:text-white/60 transition" to="/numerodoble">Numero-Doble</router-link>
            </li>
            <li v-for="num in numeros" :key="num">
                <router-link :to="'/numerodoble/' + num" class="hover:text-white/60 transition" >Doble {{ num }}</router-link>
            </li>
            <MenuTablaMultiplicar/>
        </ul>
    </div>
</template>