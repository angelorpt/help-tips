<template>
  <nav class="container navbar">
    <NuxtLink class="btn btn-primary" to="/add-field">Adicionar Campo</NuxtLink>
    <NuxtLink class="btn btn-primary" to="/autopreencher"
      >Auto Preencher</NuxtLink
    >
    <NuxtLink class="btn btn-primary" to="/hide-field"
      >Ocultar/Mostrar Campos</NuxtLink
    >
  </nav>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',
})
</script>

<style scoped>
.navbar {
  display: flex;
  justify-content: start;
  gap: 10px;
}
</style>
