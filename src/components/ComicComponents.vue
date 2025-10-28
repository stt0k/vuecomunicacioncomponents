<script setup>
// defineProps y defineEmits no necesitan importarse en <script setup>

const props = defineProps(["comic", "index"])
const emit = defineEmits(["seleccionarFavorito", "deleteComic"])

const seleccionarFavorito = () => {
    console.log(props.comic)
    emit("seleccionarFavorito", props.comic)
}

const deleteComic = () => {
    emit("deleteComic", props.index)
}

</script>
<template>
    <div class="flex flex-col justify-center gap-2">
        <h2>{{ comic.titulo }}</h2>
        <button class="bg-blue-500 p-1 rounded cursor-pointer hover:bg-blue-800 transition" v-on:click="seleccionarFavorito">Seleccionar favorito</button>
        <button v-on:click="deleteComic" class="bg-red-500 p-1 rounded cursor-pointer hover:bg-red-800 transition">Eliminar</button>
        <p>{{ comic.descripcion }}</p>
        <img class="w-32 h-32" :src="comic.imagen" />
        <h4 :class="{
            'bg-red-500': comic.year <= 2000,
            'bg-green-500': comic.year > 2000
        }">Year: {{ comic.year }}</h4>
    </div>
</template>