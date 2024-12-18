<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div id="app">
    <!-- Header -->
    <header class="bg-primary text-white py-3">
      <div class="container text-center">
        <h1>Deezer Music Client</h1>
      </div>
    </header>

    <!-- Menu -->
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <div class="container">
        
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarNav"
          aria-controls="navbarNav"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav">
            <li class="nav-item">
              <router-link class="nav-link" to="/">Home</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/playlists">Playlists</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/search">Buscador</router-link>
            </li>
          </ul>
        </div>
      </div>
    </nav>

    <!-- Main Content -->
    <main class="container my-4">
      <router-view />
    </main>

    <!-- Footer -->
    <footer class="bg-dark text-white text-center py-3">
      <p>&copy; 2024 Deezer Music Client. Todos los derechos reservados.</p>
    </footer>
  </div>
</template>

<script setup>

</script>


<style lang="scss" scoped>
nav{
  border: 1px solid gray;
}
$hover-bg-color: #007bff;
$hover-text-color: #ffffff;
li {
    padding: 0.5rem 1rem;
    cursor: pointer;
    transition: background-color 0.3s, color 0.3s;

    &:hover {
      background-color: $hover-bg-color;
      color: $hover-text-color;
      font-weight: bold;
    }
  }
</style>
