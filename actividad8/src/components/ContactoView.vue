<template>
  <div class="row justify-content-center">
    <div class="col-md-8">
      <div class="card p-4 shadow-sm">
        <h2 class="mb-3 text-center">Consulta Confidencial</h2>
        <p class="text-muted text-center mb-4">Envíenos los detalles de su caso. Nos pondremos en contacto por un canal seguro.</p>

        <form @submit.prevent="procesarConsulta">
          <div class="mb-3">
            <label class="form-label">Nombre o Seudónimo:</label>
            <input v-model="form.nombre" type="text" class="form-control" />
          </div>

          <div class="row">
            <div class="col-md-6 mb-3">
              <label class="form-label">Correo electrónico:</label>
              <input v-model="form.correo" type="email" class="form-control" />
            </div>
            <div class="col-md-6 mb-3">
              <label class="form-label">Teléfono de contacto:</label>
              <input v-model="form.telefono" type="text" class="form-control" />
            </div>
          </div>

          <div class="mb-3">
            <label class="form-label">Servicio de Interés:</label>
            <input v-model="form.servicio" type="text" class="form-control" placeholder="Ej: Seguimiento y Vigilancia" />
          </div>

          <div class="mb-3">
            <label class="form-label">Detalles del Caso / Mensaje:</label>
            <textarea v-model="form.mensaje" class="form-control" rows="4"></textarea>
          </div>

          <button type="submit" class="btn btn-dark w-100">Enviar Solicitud Segura</button>
        </form>

        <!-- Mensajes de Estado -->
        <div v-if="mensajeError" class="alert alert-danger mt-3">
          {{ mensajeError }}
        </div>

        <div v-if="consultaEnviada" class="alert alert-success mt-3">
          <h5 class="alert-heading">¡Consulta Recibida con Éxito!</h5>
          <hr />
          <p><strong>Solicitante:</strong> {{ resumen.nombre }}</p>
          <p><strong>Contacto:</strong> {{ resumen.correo }} / {{ resumen.telefono }}</p>
          <p><strong>Servicio:</strong> {{ resumen.servicio }}</p>
          <p class="mb-0"><small>Nos comunicaremos a la brevedad bajo protocolo de alta discreción.</small></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const form = ref({
  nombre: '',
  correo: '',
  telefono: '',
  servicio: '',
  mensaje: ''
})

const mensajeError = ref('')
const consultaEnviada = ref(false)
const resumen = ref({})

const procesarConsulta = () => {
  if (!form.value.nombre || !form.value.correo || !form.value.telefono || !form.value.servicio || !form.value.mensaje) {
    mensajeError.value = 'Todos los campos son obligatorios para procesar la consulta.'
    consultaEnviada.value = false
    return
  }

  mensajeError.value = ''
  consultaEnviada.value = true
  resumen.value = { ...form.value }

  form.value = { nombre: '', correo: '', telefono: '', servicio: '', mensaje: '' }
}
</script>