<template>
    <div :style="{ backgroundColor: getColor(gravedad), color: getTextColor(gravedad) }" class="tarjeta">
        <h3>{{ paciente }}</h3>
        <p>{{ fecha }} - {{ hora }}</p>
        <p>Gravedad: {{ gravedad }}</p>
        <p>{{ motivo }}</p>
        <button @click="$emit('eliminarCita')">Eliminar</button>
    </div>
</template>

<script>
export default {
    props: ['paciente', 'fecha', 'hora', 'gravedad', 'motivo'],
    methods: {
        getColor(gravedad) {
            switch (gravedad) {
                case 'baja':
                    return 'green';
                case 'media':
                    return 'yellow';
                case 'alta':
                    return 'red';
                default:
                    return 'white';
            }
        },
        getTextColor(gravedad) {
            return gravedad === 'alta' ? 'white' : 'black';
        },
    },
};
</script>

<style scoped>
.tarjeta {
    border-radius: 5px;
    padding: 15px;
    margin: 10px; 
    font-size: 16px;
    display: flex;
    flex-direction: column;
    justify-content: space-between; 
    flex: 0 0 calc(25% - 20px); 
    box-sizing: border-box; 
}
.tarjeta button {
    margin-top: 10px;
    background-color: white;
    color: black;
    border: none;
    border-radius: 5px;
    padding: 5px 10px;
    cursor: pointer;
}
.tarjeta button:hover {
    background-color: lightgray;
}
</style>
