<script setup>
// defineEmits y defineProps son macros de compilación, no necesitan importarse
// Opción 1: Definir props con tipos (recomendado)
//const props = defineProps({
    //nombredeporte: {
        //type: String,
        //required: true
    //}
//})

// Opción 2: Sintaxis más simple (también válida)
const props = defineProps(['nombredeporte'])

// Definir los eventos que este componente puede emitir
const emit = defineEmits(['seleccionarFavoritoParent'])

const seleccionarFavorito = () => {
    console.log("Soy el hijo")
    // Usar la función emit para emitir el evento
    emit('seleccionarFavoritoParent', props.nombredeporte)
}

</script>
<template>
    <div class="flex flex-col gap-5">
        <h4 class="text-red-500">{{ props.nombredeporte }}</h4>
        <button @click="seleccionarFavorito" class="mb-5 bg-blue-500 p-1 rounded hover:bg-blue-700 transition-all cursor-pointer">
            Seleccionar favorito
        </button>
    </div>
</template>