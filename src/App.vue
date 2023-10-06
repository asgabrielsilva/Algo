<script setup>
import { ref, onMounted } from 'vue'
import api from './plugins/axios'

const moviesGenres = ref([])
const TVGenres = ref([])

onMounted(async () => {
  let response = await api.get('https://api.themoviedb.org/3/genre/movie/list?language=pt-BR')
  moviesGenres.value = response.data.genres
  response =  await api.get('https://api.themoviedb.org/3/genre/tv/list?language=pt-BR')
  TVGenres.value = response.data.genres
})
</script>

<template>
  <h1>Gêneros de filmes</h1>
  <ul>
    <li v-for="genre in moviesGenres" :key="genre.id">
      {{ genre.name }} 
    </li>
  </ul>
  <hr /><hr />
  <h1>Gêneros de programas de TV</h1>
  <ul>
    <li v-for="genre in TVGenres" :key="genre.id">
      {{ genre.name }}
    </li>
  </ul>
</template>
<style scoped>

</style>
