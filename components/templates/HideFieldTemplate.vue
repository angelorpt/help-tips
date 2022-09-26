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
              {{ item.type }}
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
import { ref, computed } from 'vue'

const LISTA_API = {
  data: [
    {
      id: 1,
      type: 'DOCUMENTO FISCAL',
      description: 'Outros Documentos Fiscais',
      user_id: '361910e3-c173-c061-e053-20fb96965d02',
      created_at: '20-09-2022 14:42:39',
      updated_at: '20-09-2022 14:42:39',
    },
    {
      id: 21,
      type: 'DI',
      description: 'Documento de Importaão',
      user_id: '361910e3-c173-c061-e053-20fb96965d02',
      created_at: '23-09-2022 13:16:17',
      updated_at: '23-09-2022 13:16:17',
    },
  ],
}

export default {
  name: 'HideFieldTemplate',
  components: {},
  props: {},
  setup() {
    const selecionado = ref('')
    const listaApi = ref(LISTA_API.data)
    const idDi = computed(() => {
      const objeto = listaApi.value.find(
        (elemento) => elemento.type.toLowerCase() === 'di'
      )
      return objeto.id
    })
    return { selecionado, listaApi, idDi }
  },
  // data() {
  //   return {
  //     selecionado: '',
  //     listaApi: LISTA_API,
  //   }
  // },
  // computed: {
  //   idDi() {
  //     const objeto = this.listaApi.find(
  //       (elemento) => elemento.descricao.toLowerCase() === 'di'
  //     )
  //     return objeto.id
  //   },
  // },
}
</script>

<style lang="css" scoped></style>
