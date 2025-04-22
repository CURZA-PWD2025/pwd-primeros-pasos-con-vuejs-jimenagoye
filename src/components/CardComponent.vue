<template>
    <div class="card">
      <h2>{{ movie.title }}</h2>
      <p><strong>Director:</strong> {{ movie.director }}</p>
      <p><strong>Año:</strong> {{ movie.year }}</p>
      
      <div class="image-container">
        <img v-if="movie.poster" :src="movie.poster" alt="Portada" />
        <p v-else>Portada no disponible</p>
      </div>
  
      <button @click="toggleLike">
        {{ liked ? '💔 Quitar Like' : '❤️ Me gusta' }}
      </button>
  
      <p>Likes: {{ likes }}</p>
    </div>
  </template>
  
  <script setup>
  import { ref, defineProps, defineEmits } from 'vue'
  
  const props = defineProps({
    movie: {
      type: Object,
      required: true
    }
  })
  
  const emit = defineEmits(['update_likes'])
  
  const liked = ref(false)
  const likes = ref(props.movie.likes || 0)
  
  function toggleLike() {
    liked.value = !liked.value
    likes.value += liked.value ? 1 : -1
    emit('update_likes', likes.value)
  }
  </script>
  
  <style scoped>
  .card {
    border: 1px solid #ccc;
    padding: 1rem;
    margin: 1rem;
    border-radius: 10px;
    max-width: 300px;
  }
  .image-container {
    margin: 1rem 0;
  }
  img {
    width: 100%;
    height: auto;
  }
  button {
    background-color: #ff4081;
    color: white;
    border: none;
    padding: 0.5rem;
    border-radius: 5px;
    cursor: pointer;
  }
  </style>  