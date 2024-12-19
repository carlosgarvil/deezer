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

  
// Accede a la store
import { computed } from 'vue';
import { useUserStore } from '../stores/email';
import PiniaComponent from '../components/pinia.vue';
// Vincula datos de la store
const userStore = useUserStore();

const userEmail = computed(() => userStore.email);
const emailDomain = computed(() => userStore.emailDomain);

  </script>
  
  <style scoped>
  h1 {
    color: #007bff;
  }
  .store-data {
  border: 2px solid #007bff; /* Borde azul para destacar */
  border-radius: 10px; /* Bordes redondeados */
  background-color: #f8f9fa; /* Fondo claro */
  padding: 20px; /* Espaciado interno */
  margin-top: 20px; /* Separación del resto del contenido */
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* Sombra para resaltar */
}

.store-data h3 {
  margin-bottom: 10px; /* Espaciado entre título y contenido */
  color: #007bff; /* Color azul para el título */
}

.store-data p {
  margin: 5px 0; /* Separación entre párrafos */
  font-weight: bold; /* Texto en negrita para destacar */
}
</style>
  