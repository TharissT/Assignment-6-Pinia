<script setup>
</script>

<template> 
    <body>
        <div class="herosection">
          <img src="/src/assets/cinema.jpg" alt="Hero Image" class="hero-section">
        </div>
         <div class="my-hero-section">Welcome To BlockFlix </div>
          <div class="collage">
                <img src="/src/assets/collage.jpg" alt="Collage" class="collage">
          <div class="my-collage"> Unlimited stories one destination </div>
        </div>
    </body>
</template>

<style scoped>
body {
  background-color: black;
  margin: -10px; 
  padding: -10px;
  width: 100%; 
  position: relative;
}

.nav-buttons .button {
    background-color: #e50914;
    color: white;
    padding: 10px 20px;
    text-decoration: none;
    border-radius: 5px;
    margin-left: 10px;
    transition: background-color 0.3s;
}

.hero-section {
  position: center;
  width: 100%
}

.my-hero-section {
  position: absolute;
  top: 40%;
  left: 50%;
  transform: translate(-50%, -520%);
  font-size: 40px;
  color: black;
  font-style: bold;
  font-weight: 100;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}

.collage {
  opacity: 70%;
  position: center;
  width: 100%;
}

.my-collage {
  font-size: 100px;
  color: white;
  font-family: "Bebas Neue", sans-serif;
  position: absolute;  
  top: 50%;  
  left: 50%; 
  transform: translate(-50%, 40%);  
  text-align: center;  
}

.collage {
  opacity: 50%;
  position: center;
  width: 100%;
}
</style>