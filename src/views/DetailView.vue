<script setup>
import { useRoute, useRouter } from "vue-router";
import Header from "../components/Header.vue";
import Details from "../components/Details.vue";
import Footer from "../components/Footer.vue";

const route = useRoute();
const router = useRouter();
const movieId = route.params.id;

if (!movieId) {
  router.push("/");
}
</script>

<template>
  <Header/>
  <div class="details-view">
    <Details :id="movieId" />
    <button @click="router.push('/movies')">Back to Movies</button>
  </div>
  <Footer/>
</template>

<style scoped>
.details-view {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background-color: #121212;
}

button {
  background-color: #e50914;
  color: white;
  font-size: 1.2rem;
  padding: 12px 24px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  margin-top: 20px;
  transition: all 0.3s ease;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.6);
}

button:hover {
  background-color: #f40612;
  transform: scale(1.05);
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.8);
}

button:focus {
  outline: none;
  box-shadow: 0 0 0 4px rgba(98, 0, 234, 0.6);
}

button:active {
  background-color: #f40612;
  transform: scale(0.98);
}

button:disabled {
  background-color: #aaa;
  cursor: not-allowed;
}
</style>


