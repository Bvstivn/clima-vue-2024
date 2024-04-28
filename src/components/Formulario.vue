<template>
  <form action="" class="formulario" @submit.prevent="consultarClima">

    <Alerta v-if="error">{{ error }}</Alerta>

    <div class="campo">
      <label for="ciudad">Ciudad</label>
      <input v-model="busqueda.ciudad" type="text" id="ciudad" placeholder="ciudad" />
    </div>

    <div class="campo">
      <label for="pais">Pais</label>
      <select v-model="busqueda.pais" id="pais">
        <option value="">-- Seleccione un pais--</option>
        <option v-for="pais in paises" :value="pais.codigo">{{ pais.nombre }}</option>
      </select>
    </div>

    <input type="submit" value="Consultar Clima">
  </form>
</template>

<script setup>
//Vue
import { reactive, ref } from "vue";
//Components
import Alerta from './Alerta.vue';

//Definiciones
const emit = defineEmits(['obtener-clima']);

//Data
const busqueda = reactive({
    ciudad:'',
    pais:''
});

const error =  ref('');

const paises = [
    { codigo: 'US', nombre: 'Estados Unidos' },
    { codigo: 'MX', nombre: 'México' },
    { codigo: 'AR', nombre: 'Argentina' },
    { codigo: 'CO', nombre: 'Colombia' },
    { codigo: 'CR', nombre: 'Costa Rica' },
    { codigo: 'ES', nombre: 'España' },
    { codigo: 'PE', nombre: 'Perú' }
]

//Methods
const consultarClima = () => {
    if(Object.values(busqueda).includes('')){
        error.value = 'Todos los campos son obligatorios';
        return
    }
    error.value = '';
    emit('obtener-clima', busqueda);
}

</script>
