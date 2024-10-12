<template>
    <div class="contenedor-tarjetas">
        <p v-if="!citas.length">No hay consultas registradas</p>
        <TarjetaCita v-for="(cita, index) in citas" :key="index" :paciente="cita.paciente" :fecha="cita.fecha"
            :hora="cita.hora" :gravedad="cita.gravedad" :motivo="cita.motivo" @eliminarCita="eliminarCita(index)" />
    </div>
</template>

<script>
import TarjetaCita from './TarjetaCita.vue';

export default {
    props: ['citas'],
    components: {
        TarjetaCita,
    },
    methods: {
        eliminarCita(index) {
            this.$emit('eliminarCita', index);
        },
    },
};
</script>

<style scoped>
.contenedor-tarjetas {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
}
</style>
