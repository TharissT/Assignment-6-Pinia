<script setup>
import { ref, onMounted } from 'vue';
import { useRoute } from 'vue-router'; 
import axios from 'axios';

const route = useRoute();
const movie = ref(null);
const trailers = ref([]);

const fetchMovieDetails = async () => {
  const movieId = route.params.id;  
  try {
    const movieResponse = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?api_key=${import.meta.env.VITE_API_KEY}`);
    movie.value = movieResponse.data;

    const trailersResponse = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/videos?api_key=${import.meta.env.VITE_API_KEY}`);
    trailers.value = trailersResponse.data.results; 
  } catch (error) {
    console.error('Error fetching movie details:', error);
  }
};

onMounted(fetchMovieDetails);
</script>

<template>
  <div v-if="movie" class="movie-details">
    <h1>{{ movie.title }}</h1>

    <img 
      :src="`https://image.tmdb.org/t/p/w500${movie.poster_path}`" 
      alt="Movie Poster" 
      class="movie-poster" 
    />

    <div class="movie-info">
      <ul>
        <li><strong>Release Date:</strong> {{ movie.release_date }}</li>
        <li><strong>Runtime:</strong> {{ movie.runtime }} minutes</li>
        <li><strong>Genres:</strong> 
          {{ movie.genres.map(genre => genre.name).join(', ') }}
        </li>
        <li><strong>Rating:</strong> {{ movie.vote_average }}</li>
        <li><strong>Overview:</strong> {{ movie.overview }}</li>
        <li><strong>Budget:</strong> ${{ movie.budget.toLocaleString() }}</li>
        <li><strong>Revenue:</strong> ${{ movie.revenue.toLocaleString() }}</li>
      </ul>
    </div>

    <div v-if="trailers.length" class="trailers">
      <h2>Trailers</h2>
      <div class="trailer-list">
        <div v-for="trailer in trailers" :key="trailer.id" class="trailer-item">
          <iframe 
            :src="`https://www.youtube.com/embed/${trailer.key}`" 
            title="Trailer" 
            class="trailer-video"
            allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" 
            allowfullscreen
          ></iframe>
        </div>
      </div>
    </div>
  </div>

  <div v-else>
    <p>Loading...</p>
  </div>
</template>

<style scoped>
.movie-details {
  background-color: #141414;
  color: white;
  padding: 20px;
  min-height: 100vh;
}

h1 {
  font-size: 2rem;
  text-align: center;
}

.movie-poster {
  width: 300px;
  height: auto;
  display: block;
  margin: 20px auto;
  border-radius: 8px;
}

.movie-info {
  margin-top: 20px;
}

.movie-info ul {
  list-style-type: none;
  padding: 0;
}

.movie-info li {
  font-size: 1.1rem;
  margin-bottom: 15px;
}

.movie-info li strong {
  color: #e50914;
}

.trailers {
  margin-top: 30px;
  text-align: center;
}

.trailer-list {
  display: flex;
  justify-content: center;
  gap: 20px;
  flex-wrap: wrap;
}

.trailer-item {
  width: 300px;
}

.trailer-video {
  width: 100%;
  height: 180px;
  border-radius: 8px;
}
</style>
