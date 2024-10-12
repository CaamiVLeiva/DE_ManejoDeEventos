<template>
  <div id="app">
    <FormularioCita @agregarCita="agregarCita" />
    <ListaCitas :citas="citas" @eliminarCita="eliminarCita" />
  </div>
</template>

<script>
import FormularioCita from './components/FormularioCita.vue';
import ListaCitas from './components/ListaCitas.vue';

export default {
  components: {
    FormularioCita,
    ListaCitas,
  },
  data() {
    return {
      citas: [],
    };
  },
  methods: {
    agregarCita(nuevaCita) {
      this.citas.push(nuevaCita);
    },
    eliminarCita(index) {
      this.citas.splice(index, 1);
    },
  },
};
</script>
