<template>
    <form @submit.prevent="handleSubmit" class="formulario-cita">
        <div class="form-group">
            <label :style="{ color: !paciente ? 'red' : 'black' }">Paciente:</label>
            <input v-model="paciente" @input="validateInput" />
        </div>

        <div class="form-group">
            <label :style="{ color: !fecha ? 'red' : 'black' }">Fecha:</label>
            <input type="date" v-model="fecha" @input="validateInput" />
        </div>

        <div class="form-group">
            <label :style="{ color: !hora ? 'red' : 'black' }">Hora:</label>
            <input type="time" v-model="hora" @input="validateInput" />
        </div>

        <div class="form-group">
            <label :style="{ color: !gravedad ? 'red' : 'black' }">Gravedad:</label>
            <select v-model="gravedad" @input="validateInput">
                <option value="" disabled>Seleccione</option>
                <option value="baja">Baja</option>
                <option value="media">Media</option>
                <option value="alta">Alta</option>
            </select>
        </div>

        <div class="form-group">
            <label :style="{ color: !motivo ? 'red' : 'black' }">Motivo:</label>
            <input v-model="motivo" @input="validateInput" />
        </div>

        <button :disabled="!isFormValid" type="submit">Agregar</button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            paciente: '',
            fecha: '',
            hora: '',
            gravedad: '',
            motivo: '',
        };
    },
    computed: {
        isFormValid() {
            return this.paciente && this.fecha && this.hora && this.gravedad && this.motivo;
        },
    },
    methods: {
        validateInput() {
            // Logic to handle input validation
        },
        handleSubmit() {
            const nuevaCita = {
                paciente: this.paciente,
                fecha: this.fecha,
                hora: this.hora,
                gravedad: this.gravedad,
                motivo: this.motivo,
            };
            this.$emit('agregarCita', nuevaCita);
            this.resetForm();
        },
        resetForm() {
            this.paciente = '';
            this.fecha = '';
            this.hora = '';
            this.gravedad = '';
            this.motivo = '';
        },
    },
};
</script>

<style scoped>
.formulario-cita {
    background-color: white; 
    border: 1px solid #ccc; 
    border-radius: 5px; 
    padding: 15px; 
    margin: auto;
    max-width: 100vh; 
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1); 
    display: flex; 
    flex-wrap: nowrap;
    justify-content: space-between; 
}

.form-group{
    padding: 10px;
}

.form-group label {
    margin-right: 10px; 
    width: 150px;
    text-align: right; 
}

.formulario-cita input,
.formulario-cita select {
    flex-grow: 1; 
    padding: 10px; 
    border: 1px solid #ccc;
    border-radius: 5px; 
    box-sizing: border-box; 
}

.formulario-cita button {
    background-color: #28a745; 
    color: white; 
    border: none; 
    border-radius: 5px; 
    padding: 10px; 
    cursor: pointer; 
    margin-top: 15px;
    max-height: 50px;
}

.formulario-cita button:disabled {
    background-color: #ccc;
    cursor: not-allowed; 
}
</style>
