<script setup>

</script>

<template> 
    <body>
        <div class="topnav">
            <a class="active" href="#home">Home</a>
            <a href="#news">New Content</a>
            <a href="#contact">Who's Watching</a>
            <a href="#about">Settings</a>
        </div>
        <div class="herosection">
            <img src="/src/assets/cinema.jpg" alt="Hero Image" class="hero-section">
        <div class="myherosection">Welcome To BlockFlix</div>
        </div>
            <div class="collage">
                <img src="/src/assets/collage.jpg" alt="Collage" class="collage">
            <div class="my-collage"> Unlimited stories one destination </div>
        </div>
        <div class="signbuttons">
    <button type="button" onclick="alert('Hello, enter your account details!')">Sign In</button>
    <button type="button" onclick="alert('Dont have an account? Sign Up Now!')">Sign Up</button>
        </div>
    </body>
</template>

<style scoped>

.hero-section {
  position: center;
  width: 100%
}
.collage {
  opacity: 70%;
  position: center;
  width: 100%;
}

.my-collage {
  font-size: 75px;
  color: white;
  font-family: "Bebas Neue", sans-serif;
  position: center;
  text-align: center;
  top: 20%;
  transform: translate(5%, -400%);
}


</style>