<template>
    <div>
      <h1>Home</h1>
      <p>Bienvenido a la aplicación Deezer Music Client.</p>
    </div>
    <!-- Integrar el componente Pinia -->
    <PiniaComponent />

    <!-- Mostrar datos de la store directamente -->
    <div class="store-data">
      <h3>Datos desde la Store:</h3>
      <p>Email actual: {{ userEmail }}</p>
      <p>Dominio del email: {{ emailDomain }}</p>
    </div>
</template>
  
  <script setup>
  import { useUserStore } from '../stores/email.js';
  import PiniaComponent from '../components/pinia.vue';
  
// Accede a la store
const userStore = useUserStore();

// Vincula datos de la store
const userEmail = computed(() => userStore.email);
const emailDomain = computed(() => userStore.emailDomain);

  </script>
  
  <style scoped>
  h1 {
    color: #007bff;
  }
  </style>
  