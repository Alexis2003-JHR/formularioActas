<script setup>
import FormDoc from '../components/FormDoc.vue'
import ListDoc from '../components/ListDoc.vue'
</script>

<template>
  <div class="panel-actas">
    <h1>ACTAS DE REUNIÓN</h1>
    <div class="control-components">
      <button @click="controlState = false">Lista de Actas</button>
      <button @click="controlState = true">Crear Acta</button>
      <ListDoc v-show="!controlState"/>
      <FormDoc v-show="controlState"/>
    </div>
    <div class="view-components">

    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      controlState: true
    }
  }
}
</script>
