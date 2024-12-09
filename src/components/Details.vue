<script setup>
import axios from "axios";
import { ref, onMounted, watch } from "vue";

const props = defineProps({
  id: {
    type: String,
    required: true,
  },
});

const movieDetails = ref(null);
const trailers = ref([]);

async function fetchMovieDetails(id) {
  if (!id) return;


  const response = await axios.get(
    `https://api.themoviedb.org/3/movie/${id}?api_key=${import.meta.env.VITE_API_KEY}`
  );
  movieDetails.value = response.data;

  const trailerResponse = await axios.get(
    `https://api.themoviedb.org/3/movie/${id}/videos?api_key=${import.meta.env.VITE_API_KEY}`
  );
  trailers.value = trailerResponse.data.results;

  const boxOfficeResponse = await axios.get(
    `https://api.themoviedb.org/3/movie/${id}/revenue?api_key=${import.meta.env.VITE_API_KEY}`
  );
  boxOffice.value = boxOfficeResponse.data.revenue;
}

onMounted(() => fetchMovieDetails(props.id));
watch(() => props.id, (newId) => fetchMovieDetails(newId));
</script>

<template>
  <div class="details-component">
    <div v-if="movieDetails">
      <div class="poster-container">
        <img
          :src="`https://image.tmdb.org/t/p/w500${movieDetails.poster_path}`"
          :alt="movieDetails.title"
          class="movie-poster"
        />
      </div>
      <div class="details-content">
        <h1>{{ movieDetails.title }}</h1>
        <p class="overview">{{ movieDetails.overview }}</p>
        <p>Release Date: {{ movieDetails.release_date }}</p>
        <p>Rating: {{ movieDetails.vote_average }}/10</p>
        <p>Genres:
          <span v-for="genre in movieDetails.genres" :key="genre.id">
            {{ genre.name }}
          </span>
        </p>
        <p>Runtime: {{ movieDetails.runtime }} minutes</p>
        <div v-if="trailers.length > 0">
          <h2>Trailers:</h2>
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
    </div>
  </div>
</template>

<style scoped>
.details-component {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: #141414;
  color: #fff;
  padding: 20px;
}

.poster-container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.movie-poster {
  width: 300px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.8);
}

.details-content {
  max-width: 800px;
  margin-left: 30px;
  text-align: left;
  background-color: #1c1c1c;
  border-radius: 12px;
  padding: 30px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.6);
}

h1 {
  font-size: 2rem;
  margin: 0;
  color: #fff;
  font-weight: bold;
}

p {
  margin: 10px 0;
  line-height: 1.6;
  font-size: 1rem;
}

p span {
  margin-right: 10px;
  background-color: #333;
  padding: 5px 8px;
  border-radius: 6px;
  font-size: 0.9rem;
  color: #fff;
}

p span:hover {
  background-color: #e50914;
}

.details-content h2 {
  font-size: 1.2rem;
  margin-top: 20px;
  color: #bbb;
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
  height: 200px;
  border-radius: 8px;
}

.overview {
  font-size: 1.1rem;
  font-style: italic;
  color: #ccc;
}
</style>
