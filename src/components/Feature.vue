<script setup>
import axios from "axios";
const response = await axios.get(`https://api.themoviedb.org/3/movie/now_playing?api_key=${import.meta.env.VITE_API_KEY}`);
</script>

<template>
  <div class="movie-gallery">
    <h1>Now Playing</h1>
    <div class="movie-list">
      <div v-for="movie in response.data.results" :key="movie.id" class="movie-card" @click="getMovieDetails(movie.id)">
        <img :src="`https://image.tmdb.org/t/p/w500${movie.poster_path}`" alt="Movie Poster" class="movie-poster" />
        <p class="movie-title">{{ movie.title }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.movie-gallery {
  padding: 20px;
  color: white;
  background-color: #141414;
}

.movie-gallery h1 {
  text-align: center;
  margin-bottom: 20px;
  font-size: 2.5rem;
}

.movie-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
}

.movie-card {
  background-color: #222;
  border-radius: 10px;
  overflow: hidden;
  transition: transform 0.2s;
  width: 200px;
}

.movie-card:hover {
  transform: scale(1.05);
}

.movie-poster {
  width: 100%;
  height: auto;
}

.movie-title {
  padding: 10px;
  text-align: center;
  font-size: 1.1rem;
  color: #e50914;
}
</style>