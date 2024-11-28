<script setup>

</script>

<template> 
    <div class= header> 
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

.button {
    display: flex;
    justify-content: center;
    text-align: center; 
    width: 60px;
    margin: 20px;
    padding: 10px;
    background-color: darkgray;
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