<script setup>
import axios from "axios";
import { ref, onMounted } from "vue";

const movies = ref([]);

onMounted(async () => {
  const response = await axios.get(`https://api.themoviedb.org/3/movie/now_playing?api_key=${import.meta.env.VITE_API_KEY}`);
  movies.value = getRandomMovies(response.data.results, 3);
});

const getRandomMovies = (moviesArray, count) => {
  const shuffled = [...moviesArray].sort(() => 0.5 - Math.random());
  return shuffled.slice(0, count);
};

const getMovieDetails = (id) => {
  console.log(`Movie ID: ${id}`);
};
</script>

<template>
  <div class="movie-gallery">
    <h1>Now Playing</h1>
    <div class="movie-list">
      <div v-for="movie in movies" :key="movie.id" class="movie-card" @click="getMovieDetails(movie.id)">
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
  background-color: #000000;
}

.movie-gallery h1 {
  text-align: center;
  margin-bottom: 20px;
  font-size: 2.5rem;
  color: #e50914;
}

.movie-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 30px;
}

.movie-card {
  background-color: #333;
  border-radius: 15px;
  overflow: hidden;
  transition: transform 0.3s, box-shadow 0.3s;
  width: 220px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
}

.movie-card:hover {
  transform: scale(1.05);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.5);
}

.movie-poster {
  width: 100%;
  height: 300px;
  object-fit: cover;
}

.movie-title {
  padding: 15px;
  text-align: center;
  font-size: 1.2rem;
  font-weight: bold;
  color: #e50914;
  background-color: #222;
  border-radius: 0 0 15px 15px;
}
</style>