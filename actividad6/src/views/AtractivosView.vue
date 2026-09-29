<template>
  <div class="container">
    <h2>Atractivos Turísticos</h2>
    <div class="grid">
      <TarjetaLugar 
        v-for="lugar in listaAtractivos" 
        :key="lugar.id"
        :titulo="lugar.titulo"
        :descripcion="lugar.descripcion"
        :imagen="lugar.imagen"
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
      listaAtractivos: [
        { id: 1, titulo: 'Catedral de Chillán', descripcion: 'Icono arquitectónico de la ciudad.', imagen: 'https://via.placeholder.com/300' },
        { id: 2, titulo: 'Termas de Chillán', descripcion: 'Centro termal y de esquí en la cordillera.', imagen: 'https://via.placeholder.com/300' },
        { id: 3, titulo: 'Valle Las Trancas', descripcion: 'Naturaleza y deportes de montaña.', imagen: 'https://via.placeholder.com/300' },
        { id: 4, titulo: 'Feria de Chillán', descripcion: 'Tradición artesanal y agrícola.', imagen: 'https://via.placeholder.com/300' }
      ]
    }
  }
}
</script>