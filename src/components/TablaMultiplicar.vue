<script setup>
import { useRoute } from "vue-router"
import { watch } from "vue"

const route = useRoute()

let numero = route.params.numero ? parseInt(route.params.numero) : 0

watch(
    () => route.params.numero,
    (newNum) => {
        numero = newNum ? parseInt(newNum) : 0
    }
    )
</script>
<template>
    <div class="max-w-2xl mx-auto mt-20">
        <h2 class="text-2xl font-semibold text-gray-100 text-center mb-6">
            Tabla de multiplicar del {{ numero }}
        </h2>
        <div class="bg-black/20 rounded-lg border text-center border-black/10 overflow-hidden">
            <table class="w-full">
                <thead class="bg-black/30">
                    <tr>
                        <th class="px-6 py-4 text-sm font-medium text-gray-200 uppercase tracking-wider border-r border-black/30">
                            Operación
                        </th>
                        <th class="px-6 py-4 text-sm font-medium text-gray-200 uppercase tracking-wider">
                            Resultado
                        </th>
                    </tr>
                </thead>
                <tbody class="divide-y divide-black/30">
                    <tr v-for="i in 10" :key="i" class="hover:bg-gray-750">
                        <td class="px-6 py-4 text-sm font-medium text-gray-300 border-r border-black/30">
                            {{ numero }} × {{ i }}
                        </td>
                        <td class="px-6 py-4 text-sm font-semibold text-white">
                            {{ numero * i }}
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>