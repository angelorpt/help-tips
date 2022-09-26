<template>
  <div class="container">
    <NuxtLink class="col-2 btn btn-secondary" to="/">Home</NuxtLink>
    <h1 class="col-10">Mostrar/Ocultar Campos</h1>

    <div class="row">
      <form class="col-12" @submit.prevent.stop>
        <div class="input-group mb-3">
          <span class="input-group-text">Seleção</span>
          <select v-model="selecionado" class="form-select">
            <option disabled hidden value="">Selecione</option>
            <option value="1">Opção 1</option>
            <option value="2">Opção 2</option>
            <option value="di">DI</option>
          </select>
          <div class="ml-3">Valor Selecionado: {{ selecionado }}</div>
        </div>

        <div v-if="selecionado === 'di'" class="input-group mb-3">
          <span class="input-group-text">DI 1</span>
          <input type="text" class="form-control" />
        </div>

        <div v-if="selecionado === 'di'" class="input-group mb-3">
          <span class="input-group-text">DI 2</span>
          <input type="text" class="form-control" />
        </div>

        <div v-if="selecionado !== 'di'" class="input-group mb-3">
          <span class="input-group-text">Não DI</span>
          <input type="text" class="form-control" />
        </div>

        <div class="input-group mb-3">
          <span class="input-group-text">Sempre</span>
          <input type="text" class="form-control" />
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HideFieldTemplate',
  components: {},
  props: {},
  data() {
    return {
      selecionado: '',
    }
  },
}
</script>

<style lang="css" scoped></style>
