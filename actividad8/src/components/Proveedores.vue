<script setup>
import { ref, computed } from 'vue'
import { useRecepcionStore } from '../stores/useRecepcionStore.js'

const { state } = useRecepcionStore()

const form = ref({ nombre: '', rut: '', contacto: '' })

function guardar() {
  if (!form.value.nombre || !form.value.rut) {
    alert('Por favor, complete al menos el nombre y el RUT del proveedor.')
    return
  }

  state.proveedores.push({
    id: Date.now(),
    nombre: form.value.nombre,
    rut: form.value.rut,
    contacto: form.value.contacto
  })

  // Limpiar formulario
  form.value = { nombre: '', rut: '', contacto: '' }
}

const listaProveedores = computed(() => state?.proveedores || [])
</script>

<template>
  <div>
    <h2>Proveedores</h2>

    <form @submit.prevent="guardar">
      <input v-model="form.nombre" placeholder="Nombre de la Editorial / Proveedor" />
      <input v-model="form.rut" placeholder="RUT (ej: 76.123.456-7)" />
      <input v-model="form.contacto" placeholder="Correo o Teléfono de Contacto" />
      <button type="submit">Agregar Proveedor</button>
    </form>

    <table class="table">
      <thead>
        <tr>
          <th>#</th>
          <th>Nombre</th>
          <th>RUT</th>
          <th>Contacto</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="p in listaProveedores" :key="p.id">
          <td>{{ p.id }}</td>
          <td>{{ p.nombre }}</td>
          <td>{{ p.rut }}</td>
          <td>{{ p.contacto || '—' }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped>
.table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 16px;
}
.table th, .table td {
  border: 1px solid #ddd;
  padding: 8px;
  text-align: left;
}
.table th {
  background-color: #f4f4f5;
}
form {
  display: flex;
  gap: 8px;
  margin-bottom: 16px;
  flex-wrap: wrap;
}
form input {
  padding: 6px;
}
</style>