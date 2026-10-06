<script setup>
import { ref } from 'vue'
import { useRecepcionStore } from '../stores/useRecepcionStore.js'

const { state } = useRecepcionStore()

const form = ref({ isbn: '', titulo: '', editorial: '', nivel: 'Básica', anio_publicacion: 2025 })

function guardar(){
  const len = form.value.isbn.trim().length
  if (len !== 10 && len !== 13) {
    alert('El ISBN debe tener exactamente 10 o 13 dígitos')
    return
  }

  state.libros.push({ 
    id: Date.now(), 
    isbn: form.value.isbn,
    titulo: form.value.titulo,
    editorial: form.value.editorial,
    nivel: form.value.nivel,
    anio: form.value.anio 
  })
  
  form.value = { isbn: '', titulo: '', editorial: '', nivel: 'Básica', anio: 2025 }
}
</script>

<template>
  <div>
    <h2>Libros</h2>
    <form @submit.prevent="guardar">
      <input v-model="form.isbn" placeholder="ISBN" />
      <input v-model="form.titulo" placeholder="Título" />
      <input v-model="form.editorial" placeholder="Editorial" />
      <select v-model="form.nivel">
        <option>Básica</option>
        <option>Media</option>
      </select>
      <input v-model.number="form.anio_publicacion" type="number" placeholder="Año" />
      <button type="submit">Agregar</button>
    </form>

    <ul>
      <li v-for="l in state?.libros || []" :key="l.id">{{ l.titulo }} - {{ l.isbn }} - {{ l.anio ?? l.anio_publicacion }}</li>
    </ul>
  </div>
</template>
