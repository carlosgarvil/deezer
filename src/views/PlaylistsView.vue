<template>
    <div>
      <h1>Playlists</h1>
      <p>Gestiona tus playlists aquí.</p>
    </div>
  
    <div class="playlist-page container">
    <h1 class="text-center my-4">Gestión de Playlists</h1>

    <!-- Tarjetas (Cards) -->
    <div class="row">
      <div class="col-md-4" v-for="(playlist, index) in playlists" :key="index">
        <div class="card mb-4 shadow-sm">
          <div class="card-body">
            <h5 class="card-title">{{ playlist.name }}</h5>
            <p class="card-text">Canciones: {{ playlist.songs.length }}</p>
            <button class="btn btn-primary" @click="viewPlaylist(playlist)">
              Ver Playlist
            </button>
            <button
              type="button"
              class="btn btn-danger"
              @click="deletePlaylist"
              data-bs-dismiss="modal"
            >
              Borrar
            </button>
          </div>
        </div>
      </div>
    </div>

    <!-- Botón con Dropdown -->
    <div class="dropdown my-4">
      <button
        class="btn btn-secondary dropdown-toggle"
        type="button"
        id="dropdownMenuButton"
        data-bs-toggle="dropdown"
        aria-expanded="false"
      >
        Opciones de Playlist
      </button>
      <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton">
        <li><a class="dropdown-item" href="#">Crear nueva playlist</a></li>
        <li><a class="dropdown-item" href="#">Eliminar playlist</a></li>
        <li><a class="dropdown-item" href="#">Exportar playlist</a></li>
      </ul>
    </div>

    <!-- Input y Botón -->
    <div class="input-group mb-3">
      <input
        type="text"
        class="form-control"
        placeholder="Nombre de la nueva playlist"
        aria-label="Nueva Playlist"
        aria-describedby="button-addon2"
        v-model="newPlaylistName"
      />
      <button
        class="btn btn-success"
        type="button"
        id="button-addon2"
        @click="addPlaylist"
      >
        Crear Playlist
      </button>
      <button
                class="btn btn-danger"
                @click="openDeleteModal(playlist, index)"
              >
                Borrar Playlist
              </button>
    </div>

    <!-- Alerta -->
    <div v-if="alertMessage" class="alert alert-success" role="alert">
      {{ alertMessage }}
    </div>
  </div>
  <!-- Modal de Confirmación -->
  <div
      class="modal fade"
      id="deleteModal"
      tabindex="-1"
      aria-labelledby="deleteModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="deleteModalLabel">Confirmar Borrado</h5>
            <button
              type="button"
              class="btn-close"
              data-bs-dismiss="modal"
              aria-label="Close"
            ></button>
          </div>
          <div class="modal-body">
            ¿Estás seguro de que quieres borrar la playlist
            <strong>{{ selectedPlaylist?.name }}</strong>?
          </div>
          <div class="modal-footer">
            <button
              type="button"
              class="btn btn-secondary"
              data-bs-dismiss="modal"
            >
              Cancelar
            </button>
        
          </div>
        </div>
      </div>
    </div>
  
  
  </template>
  
  <script setup>
  import { ref } from 'vue';

// Estado de playlists y datos relacionados
const playlists = ref([
  { name: 'Rock Clásico', songs: ['Bohemian Rhapsody', 'Hotel California'] },
  { name: 'Pop Hits', songs: ['Shape of You', 'Blinding Lights'] },
]);

const newPlaylistName = ref('');
const alertMessage = ref('');

// Funciones
const addPlaylist = () => {
  if (newPlaylistName.value.trim() !== '') {
    playlists.value.push({ name: newPlaylistName.value, songs: [] });
    alertMessage.value = `La playlist "${newPlaylistName.value}" ha sido creada.`;
    newPlaylistName.value = '';
    setTimeout(() => (alertMessage.value = ''), 3000);
  }
};

const viewPlaylist = (playlist) => {
  alert(`Abriendo playlist: ${playlist.name}`);
};
  </script>
  
  <style scoped>
  h1 {
    color: #28a745;
  }
  .playlist-page {
  padding: 20px;
}

.card {
  transition: transform 0.2s;
}

.card:hover {
  transform: scale(1.05);
}
  </style>
  