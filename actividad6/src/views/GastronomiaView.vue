<template>
  <div class="container">
    <h2>Gastronomía Local</h2>
    <div class="grid">
      <TarjetaLugar 
        v-for="plato in listaGastronomia" 
        :key="plato.id"
        :titulo="plato.titulo"
        :descripcion="plato.descripcion"
        :imagen="plato.imagen"
      />
    </div>
  </div>
</template>

<script>
import TarjetaLugar from '../components/TarjetaLugar.vue'

export default {
  components: { TarjetaLugar },
  data() {
    return {
      listaGastronomia: [
        { id: 1, titulo: 'Longanizas de Chillán', descripcion: 'Producto típico con denominación de origen.', imagen: 'https://via.placeholder.com/300' },
        { id: 2, titulo: 'Pan Amasado', descripcion: 'Tradición horneada en barro.', imagen: 'https://via.placeholder.com/300' },
        { id: 3, titulo: 'Vinos del Valle del Itata', descripcion: 'Vinos patrimoniales de cepas ancestrales.', imagen: 'https://via.placeholder.com/300' }
      ]
    }
  }
}
</script>