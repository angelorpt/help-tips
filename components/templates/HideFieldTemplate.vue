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
            <option v-for="item in listaApi" :key="item.id" :value="item.id">
              {{ item.descricao }}
            </option>
          </select>
          <div class="ml-3">Valor Selecionado: {{ selecionado }}</div>
          <div class="ml-3">ID da opção DI: {{ idDi }}</div>
        </div>

        <div v-if="selecionado === idDi" class="input-group mb-3">
          <span class="input-group-text">DI 1</span>
          <input type="text" class="form-control" />
        </div>

        <div v-if="selecionado === idDi" class="input-group mb-3">
          <span class="input-group-text">DI 2</span>
          <input type="text" class="form-control" />
        </div>

        <div v-if="selecionado !== idDi" class="input-group mb-3">
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
const LISTA_API = [
  { id: 1, descricao: 'Opção 1' },
  { id: 3, descricao: 'Opção 2' },
  { id: 33, descricao: 'DI' },
]

export default {
  name: 'HideFieldTemplate',
  components: {},
  props: {},
  data() {
    return {
      selecionado: '',
      listaApi: LISTA_API,
    }
  },
  computed: {
    idDi() {
      const objeto = this.listaApi.find(
        (elemento) => elemento.descricao.toLowerCase() === 'di'
      )
      return objeto.id
    },
  },
}
</script>

<style lang="css" scoped></style>
