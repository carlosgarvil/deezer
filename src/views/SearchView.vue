<template>
    <div>
      <h1>Buscador</h1>
      <p>Busca canciones, artistas o álbumes.</p>
    </div>
    <template>
  <div class="search-page">
    <h1>Resultados del Álbum</h1>
    <div class="album-info">
      <h2>{{ albumData.title }}</h2>
      <p><strong>Artista:</strong> {{ albumData.artist?.name }}</p>
      <p><strong>Fecha de lanzamiento:</strong> {{ albumData.release_date }}</p>
    </div>

    <div class="songs">
      <h3>Canciones</h3>
      <div class="song-cards">
        <div
          v-for="song in albumData.tracks?.data"
          :key="song.id"
          class="song-card"
        >
          <p><strong>{{ song.title }}</strong></p>
          <audio :src="song.preview" controls></audio>
        </div>
      </div>
    </div>
  </div>
</template>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue';
  
  const albumData = ref({}); // Guardará los datos del álbum
  
  // Función para obtener datos del álbum desde la API de Deezer
  const fetchAlbumData = async () => {
    try {
      const response = await fetch('https://cors-anywhere.herokuapp.com/https://api.deezer.com/album/586206062');
      if (!response.ok) throw new Error('Error al obtener los datos');
      albumData.value = await response.json();
    } catch (error) {
      console.error('Error:', error);
    }
  };
  
  // Llama a la función al montar el componente
  onMounted(fetchAlbumData);
  </script>
  
  <style scoped>
  h1 {
    color: #dc3545;
  }
  </style>
  