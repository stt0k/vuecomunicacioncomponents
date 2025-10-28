<script setup>
import { ref } from "vue"

const props = defineProps(["numero"])
const emit = defineEmits(["sumar-numero"])

const sumar = () => {
    emit("sumar-numero", props.numero)
}

</script>
<template>
    <div class="flex flex-col justify-center space-y-2">
        <h1 class="text-blue-500">Numero Hijo: <span>{{ props.numero }}</span></h1>
        <button v-on:click="sumar" class="bg-blue-500 rounded p-1 cursor-pointer">{{ props.numero }}</button>
    </div>
</template>