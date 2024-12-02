<script setup>

</script>

<template>
  <div class="hero">
    <div class="overlay">
      <div class="navbar">
        <h1>BlockFlix</h1>
        <a href="login" class="button login">Login</a>
      </div>
      <div class="form-container">
        <h2>Create an Account</h2>
        <form>
          <input type="text" placeholder="Name" class="input-field" required>
          <input type="email" placeholder="Email" class="input-field" required>
          <input type="password" placeholder="Password" class="input-field" required>
          <button type="submit" class="button register">Register</button>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>

.hero {
  background-image: url('your-image-url-here.jpg');
  background-size: cover;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  background-color: black;
}

.overlay {
  background-color: rgba(0, 0, 0, 0.8);
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  color: white;
  padding: 20px;
}

.navbar {
  width: 100%;
  display: flex;
  justify-content: space-between;
  padding: 20px;
}

.navbar h1 {
  font-size: 2.5rem;
  font-family: 'Arial', sans-serif;
  color: #e50914;
  font-weight: bold;
}

.navbar .login {
  background-color: #e50914;
  color: white;
  padding: 10px 25px;
  text-decoration: none;
  border-radius: 5px;
  font-size: 1.2rem;
  font-weight: bold;
  transition: background-color 0.3s, transform 0.2s;
}

.navbar .login:hover {
  background-color: #f40612;
  transform: scale(1.05);
}

.form-container {
  text-align: center;
  margin-top: 50px;
}

.form-container h2 {
  font-size: 2.2rem;
  color: white;
  margin-bottom: 25px;
}

.input-field {
  padding: 15px;
  width: 350px;
  border-radius: 5px;
  border: 1px solid #ccc;
  margin-bottom: 20px;
  transition: border-color 0.3s;
  background-color: #333;
  color: white;
  font-size: 1rem;
}

.input-field:focus {
  border-color: #e50914;
  outline: none;
}

.register {
  background-color: #e50914;
  color: white;
  padding: 12px 30px;
  border: none;
  border-radius: 5px;
  font-size: 1.1rem;
  cursor: pointer;
  transition: background-color 0.3s, transform 0.2s;
}

.register:hover {
  background-color: #f40612;
  transform: scale(1.05);
}

@media (max-width: 600px) {
  .input-field {
    width: 80%;
  }

  .navbar h1 {
    font-size: 2rem;
  }

  .form-container h2 {
    font-size: 1.8rem;
  }
}
</style>

