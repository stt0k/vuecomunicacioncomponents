<script setup>
import { ref, computed, onMounted } from "vue"

const numeros = ref([])
const numerosSeleccionados = ref([])

const generarRandom = () => {
    numeros.value = [] // Limpiar array anterior
    numerosSeleccionados.value = [] // Limpiar selecciones anteriores
    
    for (let i = 0; i < 8; i++) {
        let random = parseInt(Math.random() * 50) + 1
        numeros.value.push(random)
    }
}

// Se ejecuta automáticamente cuando el componente se monta
onMounted(() => {
    generarRandom()
})

// Computed property que calcula automáticamente la suma
const suma = computed(() => {
    return numerosSeleccionados.value.reduce((total, num) => total + num, 0)
})

</script>
<template>
    <div class="flex flex-col items-center justify-center gap-5 mt-10">
        <div class="flex flex-col items-center">
            <h1 class="font-bold text-2xl mb-5">Ejemplo checkbox</h1>
            <button @click="generarRandom" class="bg-blue-500 p-2 rounded cursor-pointer hover:bg-blue-700 transition text-white">Generar números</button>
        </div>
        <div class="flex flex-col gap-5">
            <div class="grid grid-cols-4 gap-3">
                <div v-for="(numero, i) in numeros" :key="i" class="flex items-center gap-2">
                    <input type="checkbox" :value="numero" v-model="numerosSeleccionados" :id="`checkbox-${i}`" />
                    <label class="cursor-pointer">Número {{ numero }}</label>
                </div>
            </div>
            <div class="text-center">
                <h1 class="text-xl font-semibold">La suma seleccionada es: <span class="text-blue-600">{{ suma }}</span></h1>
                <p class="text-gray-600">Seleccionados: {{ numerosSeleccionados.join(', ') }}</p>
            </div>
        </div>
    </div>
</template>