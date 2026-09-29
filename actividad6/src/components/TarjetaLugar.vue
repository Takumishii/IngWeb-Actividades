<template>
  <div class="card">
    <img :src="imagen" :alt="titulo" class="card-img" />
    <div class="card-body">
      <h3>{{ titulo }}</h3>
      <p>{{ descripcion }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TarjetaLugar',
  props: {
    titulo: { type: String, required: true },
    descripcion: { type: String, required: true },
    imagen: { type: String, required: true }
  }
}
</script>

<style scoped>
.card {
  border: 1px solid #ddd;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  background: #fff;
}
.card-img {
  width: 100%;
  height: 180px;
  object-fit: cover;
}
.card-body {
  padding: 1rem;
}
</style>