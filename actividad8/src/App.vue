<template>
  <div>
    <!-- Menú de pestañas con v-if -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark mb-4">
      <div class="container">
        <a class="navbar-brand" href="#">TechFix Ñuble</a>
        <div class="navbar-nav">
          <button class="btn btn-link nav-link" @click="seccion = 'inicio'">Inicio</button>
          <button class="btn btn-link nav-link" @click="seccion = 'nosotros'">Nosotros</button>
          <button class="btn btn-link nav-link" @click="seccion = 'servicios'">Servicios</button>
          <button class="btn btn-link nav-link" @click="seccion = 'contacto'">Contacto</button>
        </div>
      </div>
    </nav>

    <!-- Vistas dinámicas según la variable -->
    <main class="container">
      <InicioView v-if="seccion === 'inicio'" />
      <NosotrosView v-if="seccion === 'nosotros'" />
      <ServiciosView v-if="seccion === 'servicios'" />
      <ContactoView v-if="seccion === 'contacto'" />
    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import InicioView from './views/InicioView.vue'
import NosotrosView from './views/NosotrosView.vue'
import ServiciosView from './views/ServiciosView.vue'
import ContactoView from './views/ContactoView.vue'

const seccion = ref('inicio')
</script>