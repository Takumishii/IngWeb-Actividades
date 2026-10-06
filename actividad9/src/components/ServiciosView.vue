<template>
  <div>
    <h2 class="mb-4">Catálogo de Servicios de Investigación</h2>

    <!-- Alerta cuando se selecciona un servicio vía emit -->
    <div v-if="servicioSeleccionado" class="alert alert-info alert-dismissible fade show">
      Has seleccionado: <strong>{{ servicioSeleccionado }}</strong>. Cambia a la pestaña <strong>Contacto</strong> para realizar tu consulta.
    </div>

    <!-- Controles de Filtro -->
    <div class="row mb-4">
      <div class="col-md-6 mb-2">
        <input 
          v-model="busqueda" 
          type="text" 
          class="form-control" 
          placeholder="Buscar servicio por nombre..." 
        />
      </div>
      <div class="col-md-6">
        <select v-model="categoriaFiltro" class="form-select">
          <option value="">Todas las categorías</option>
          <option value="Particular">Particular</option>
          <option value="Corporativo">Corporativo</option>
          <option value="Tecnológico">Tecnológico</option>
        </select>
      </div>
    </div>

    <!-- Lista Filtrada -->
    <div v-if="serviciosFiltrados.length > 0" class="row">
      <div v-for="servicio in serviciosFiltrados" :key="servicio.id" class="col-md-4 mb-3">
        <ServicioCard 
          :servicio="servicio" 
          @seleccionar-servicio="capturarSeleccion" 
        />
      </div>
    </div>

    <!-- Mensaje condicional de ausencia de resultados -->
    <div v-else class="alert alert-warning text-center">
      No se encontraron servicios de investigación que coincidan con los criterios.
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import ServicioCard from './ServicioCard.vue'

const busqueda = ref('')
const categoriaFiltro = ref('')
const servicioSeleccionado = ref('')

const listaServicios = ref([
  { id: 1, nombre: 'Seguimiento y Vigilancia', categoria: 'Particular', descripcion: 'Registro fotográfico y en video de desplazamientos y rutinas.', precio: 250000, disponible: true },
  { id: 2, nombre: 'Investigación Infidelidades', categoria: 'Particular', descripcion: 'Obtención de pruebas verificables con máxima discreción.', precio: 300000, disponible: true },
  { id: 3, nombre: 'Ubicación de Personas', categoria: 'Particular', descripcion: 'Búsqueda de familiares, deudores o personas extraviadas.', precio: 180000, disponible: true },
  { id: 4, nombre: 'Auditoría Laboral/Empresarial', categoria: 'Corporativo', descripcion: 'Verificación de antecedentes de personal e investigación de hurtos internos.', precio: 400000, disponible: true },
  { id: 5, nombre: 'Análisis Forense Digital', categoria: 'Tecnológico', descripcion: 'Recuperación y rastreo de evidencia en dispositivos o redes.', precio: 350000, disponible: false },
  { id: 6, nombre: 'Barrido Electrónico de Micrófonos', categoria: 'Tecnológico', descripcion: 'Detección de dispositivos ocultos de escucha o cámaras en oficinas.', precio: 220000, disponible: true }
])

const serviciosFiltrados = computed(() => {
  return listaServicios.value.filter(s => {
    const coincideNombre = s.nombre.toLowerCase().includes(busqueda.value.toLowerCase())
    const coincideCategoria = categoriaFiltro.value === '' || s.categoria === categoriaFiltro.value
    return coincideNombre && coincideCategoria
  })
})

const capturarSeleccion = (nombreServicio) => {
  servicioSeleccionado.value = nombreServicio
}
</script>