<script setup>

</script>

<template> 
    <div class="header"> 
        <h1> BlockFlix</h1>
    </div>
    <div class="buttons">
        <RouterLink to="/register" class="button">Register</RouterLink>
        <RouterLink to="/login" class="button">Login</RouterLink>
    </div>
</template>

<style scoped>
.header {
  background-color: black; 
  padding: 20px;  
  width: 100%;  
  position: fixed;  
  top: 0;  
  left: 0;  
  z-index: 1000;  
}

.buttons {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: black; 
  padding: 20px;
  margin-top: 80px; 
}

.button {
  margin: 10px;
  padding: 10px 20px;
  background-color: #e50914; 
  color: white;
  text-decoration: none;
  border-radius: 5px;
  font-size: 1rem;
  transition: background-color 0.3s;
}

.button:hover {
  background-color: #f40612; 
}

h1 {
  color: white; 
  background-color: black;
  font-family: 'Arial', sans-serif;
  font-size: 3rem; 
  font-style: italic;
  text-align: center;
  margin: 0;
}
</style>
