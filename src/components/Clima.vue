<template>
    <div class="resultado" >
        <h2>Clima de: {{ clima.name }} </h2>
        <p class="actual" >{{ formatearTemperatura(clima.main.tem) }} &deg;C</p>
        <div class="temperaturas">
            <p>Min: <span> {{ formatearTemperatura(clima.main.temp_min) }} &deg;C</span></p>
            <p>Max: <span> {{ formatearTemperatura(clima.main.temp_max) }} &deg;C</span></p>
        </div>
    </div>
</template>

<script setup>
//Composables
import useClima from "../composables/useClima";

//Composables
const { formatearTemperatura } = useClima();

//Definiciones
defineProps({
    clima:{
        type: Object,
        required: true,
    }
});
</script>