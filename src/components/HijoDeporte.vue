<script setup>
// Opción 1: Definir props con tipos (recomendado)
//const props = defineProps({
    //nombredeporte: {
        //type: String,
        //required: true
    //}
//})

// Opción 2: Sintaxis más simple (también válida)
const props = defineProps(['nombredeporte'])

</script>
<template>
    <div>
        <h4 class="text-red-500">{{ nombredeporte }}</h4>
    </div>
</template>