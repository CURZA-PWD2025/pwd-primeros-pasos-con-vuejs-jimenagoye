<template>
  <div class="app">
    <h1>🎞️ Mis Películas Favoritas</h1>
    <div class="cards">
      <CardComponent
        v-for="(movie, index) in movies"
        :key="index"
        :movie="movie"
        @update_likes="updateLikes(index, $event)"
      />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import CardComponent from './components/CardComponent.vue'

// Array de películas
const movies = ref([
{
  "id": 1,
  "title": "Alien: El octavo pasajero",
  "anio": 1979,
  "genero": "Ciencia ficción / Terror",
  "director": "Ridley Scott",
  "poster": "https://1.bp.blogspot.com/-H_tmWbgQmaw/VcDpLpc3mbI/AAAAAAAAGec/wB7wk9Hgy4Y/s1600/alien-el-octavo-pasajero.jpg",
  "likes": 0
},
{
  "id": 2,
  "title": "Depredador",
  "director": "John McTiernan",
  "year": 1987,
  "poster": "https://upload.wikimedia.org/wikipedia/en/9/95/Predator_Movie.jpg",
  "likes": 0
},
{
  "id": 3,
  "title": "Rambo: First Blood",
  "director": "Ted Kotcheff",
  "year": 1982,
  "poster": "https://th.bing.com/th/id/OIP.kxKMKn1J3a0xu5Ta1sy3KgHaKj?rs=1&pid=ImgDetMain",
  "likes": 0
},
{
  "id": 4,
  "title": "El Pianista",
  "director": "Roman Polanski",
  "year": 2002,
  "poster": "https://upload.wikimedia.org/wikipedia/en/a/a6/The_Pianist_movie.jpg",
  "likes": 0
},
{
  "id": 5,
  "title": "Inteligencia Artificial",
  "director": "Steven Spielberg",
  "year": 2001,
  "poster": "https://th.bing.com/th/id/OIP.iGPbs9hKC-EcWXXoCB2mfQAAAA?rs=1&pid=ImgDetMain",
  "likes": 0
},
{
  "id": 6,
  "title": "Lo Bueno, lo Malo y lo Feo",
  "director": "Sergio Leone",
  "year": 1966,
  "poster": "https://img.discogs.com/uV4EuahRWnr8TO8AIPpfuUjIa6I=/fit-in/600x605/filters:strip_icc():format(jpeg):mode_rgb():quality(90)/discogs-images/R-11151022-1510791131-1540.jpeg.jpg",
  "likes": 0
}
])

function updateLikes(index, newLikes) {
  movies.value[index].likes = newLikes
}
</script>

<style scoped>
.app {
  padding: 2rem;
  text-align: center;
}

.cards {
  display: flex;
  flex-wrap: wrap;
  gap: 1.5rem;
  justify-content: center;
}
</style>