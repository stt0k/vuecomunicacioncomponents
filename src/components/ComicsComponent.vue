<script setup>
import ComicComponents from "./ComicComponents.vue";
import { ref } from "vue"

const comicFavorito = ref([])
const comicForm = ref({
    titulo: "",
    imagen: "",
    descripcion: "",
    year: 0
})

const seleccionarFavorito = (comic) => {
    console.log(comic.titulo)
    comicFavorito.value.push(comic)
}

const createComic = () => {
    comics.value.push(comicForm.value)
}

const deleteComic = (index) => {
    comics.value.splice(index, 1)
}

const comics = ref([
                {
                titulo: "Spiderman",
                imagen:
                    "https://3.bp.blogspot.com/-i70Zu_LAHwI/T290xxduu-I/AAAAAAAALq8/8bXDrdvW50o/s1600/spiderman1.jpg",
                descripcion: "Hombre araña"
                , year: 1997
                },
                {
                titulo: "Wolverine",
                imagen:
                    "https://images-na.ssl-images-amazon.com/images/I/51c1Q1IdUBL._SX259_BO1,204,203,200_.jpg",
                descripcion: "Lobezno"
                , year: 2003
                },
                {
                titulo: "Guardianes de la Galaxia",
                imagen:
                    "https://images-na.ssl-images-amazon.com/images/I/51c1Q1IdUBL._SX259_BO1,204,203,200_.jpg",
                descripcion: "Yo soy Groot"
                , year: 2006
                },
                {
                titulo: "Avengers",
                imagen:
                    "https://d26lpennugtm8s.cloudfront.net/stores/057/977/products/ma_avengers_01_01-891178138c020318f315132687055371-640-0.jpg",
                descripcion: "Los Vengadores"
                , year: 1993
                },
                {
                titulo: "Spawn",
                imagen:
                    "https://i.pinimg.com/originals/e1/d8/ff/e1d8ff4aeab5e567798635008fe98ee1.png",
                descripcion: "Al Simmons"
                , year: 2000
                },
                {
                titulo: "Batman",
                imagen:
                    "https://www.comicverso.com/wp-content/uploads/2020/06/The-Killing-Joke-657x1024.jpg",
                descripcion: "Murcielago"
                , year: 2001
                }
])

</script>
<template>
        <div class="flex flex-col justify-center items-center mt-10">
            <h2 class="text-2xl font-bold mb-10">Padre comics</h2>
            <form v-on:submit.prevent="createComic" class="flex flex-col mb-5 justify-center gap-2" action="">
                <label>Titulo</label>
                <input class="border rounded" type="text" v-model="comicForm.titulo">
                <label>Imagen</label>
                <input class="border rounded" type="text" v-model="comicForm.imagen">
                <label>Descripción</label>
                <input class="border rounded" type="text" v-model="comicForm.descripcion">
                <label>Año</label>
                <input class="border rounded" type="number" v-model="comicForm.year">
                <button class="bg-blue-500 p-1 rounded cursor-pointer">Nuevo comic</button>
            </form>
            <h3 class="text-xl font-semibold mb-5">Comics Favoritos 
                <span v-for="comic in comicFavorito" :key="comic.titulo" class="mx-2">{{ comic.titulo }}</span>
            </h3>
        <div class="mb-10" id="comics" v-for="(comic, i) in comics" :key="comic">
            <ComicComponents :comic="comic" :index="i" @deleteComic="deleteComic" @seleccionarFavorito="seleccionarFavorito" />
        </div>
    </div>
</template>