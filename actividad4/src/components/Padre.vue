<template>
    <div>
        <Hijo mensaje="Hola desde el padre" />
    </div>
    <div>
        <HijoBoton @saludo="mostrarSaludo" />
        <p v-if="mensaje">{{ mensaje }}</p>
    </div>
    <div>
        <Contacto />
    </div>
    <div>
        <Tareas />
    </div>
</template>
<script>
import Hijo from './Hijo.vue'
import HijoBoton from './HijoBoton.vue'
import Contacto from './Contacto.vue'
import Tareas from './Tareas.vue'
export default {
    components: {
        Hijo,
        HijoBoton,
        Contacto,
        Tareas
    },
    data() {
        return {
            mensaje: ''
        }
    },
    methods: {
        mostrarSaludo() {
            this.mensaje = '¡Hola desde el hijo!'
        }
    }
}
</script>