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
</template>
<script>
import Hijo from './Hijo.vue'
import HijoBoton from './HijoBoton.vue'
import Contacto from './Contacto.vue'
export default {
    components: {
        Hijo,
        HijoBoton,
        Contacto
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