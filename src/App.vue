<template>
  <h1 class="titulo">Buscador de Clima</h1>
  <div class="contenedor buscador-clima"></div>
  <Formulario @obtener-clima="obtenerClima" />
  <Spinner v-if="cargando" />
  <Alerta v-if="error">{{ error }}</Alerta>
  <Clima v-if="mostrarClima" :clima="clima" />
</template>

<script setup>
//Components
import Formulario from './components/Formulario.vue';
import Clima from './components/Clima.vue';
import Spinner from './components/Spinner.vue';
import Alerta from './components/Alerta.vue';

//Composables
import useClima from '../composables/useClima';

//Composables
const { obtenerClima, clima, mostrarClima, cargando, error } = useClima();

</script>