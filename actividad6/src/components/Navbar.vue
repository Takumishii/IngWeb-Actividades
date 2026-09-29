<template>
  <nav class="navbar">
    <div class="logo">Turismo Chillán</div>
    <ul class="nav-links">
      <li><router-link to="/">Inicio</router-link></li>
      <li><router-link to="/atractivos">Atractivos</router-link></li>
      <li><router-link to="/gastronomia">Gastronomía</router-link></li>
      <li><router-link to="/contacto">Contacto</router-link></li>
    </ul>
  </nav>
</template>

<style scoped>
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #8B0000; /* Rojo artesanal / Terracota */
  padding: 1rem 2rem;
  color: white;
}
.nav-links {
  list-style: none;
  display: flex;
  gap: 1.5rem;
}
.nav-links a {
  color: white;
  text-decoration: none;
  font-weight: bold;
}
.nav-links a.router-link-active {
  border-bottom: 2px solid #FFD700;
}
</style>