<template>
  <div class="container">
    <NuxtLink class="col-2 btn btn-secondary" to="/">Home</NuxtLink>
    <h1 class="col-10">Auto preencher</h1>

    <div class="row">
      <form class="col-12" @submit.prevent.stop>
        <div class="input-group mb-3">
          <span class="input-group-text">CEP</span>
          <input
            v-model="cep"
            type="text"
            class="form-control"
            aria-label="Cep"
            @blur="consultarCep"
          />
        </div>

        <div class="input-group mb-3">
          <span class="input-group-text">Endereço</span>
          <input
            v-model="endereco"
            type="text"
            class="form-control"
            aria-label="Endereço"
          />
        </div>

        <div class="input-group mb-3">
          <span class="input-group-text">Cidade</span>
          <input
            v-model="cidade"
            type="text"
            class="form-control"
            aria-label="Cidade"
          />
        </div>

        <div class="input-group mb-3">
          <span class="input-group-text">UF</span>
          <input
            v-model="uf"
            type="text"
            class="form-control"
            aria-label="UF"
          />
        </div>

        <div class="input-group mb-3">
          <span class="input-group-text">Bairro</span>
          <input
            v-model="bairro"
            type="text"
            class="form-control"
            aria-label="Endereço"
          />
        </div>

        <div class="input-group mb-3">
          <span class="input-group-text">ddd</span>
          <input
            v-model="ddd"
            type="text"
            class="form-control"
            aria-label="Endereço"
          />
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'AutoPrencherTemplate',
  components: {},
  props: {},
  data() {
    return {
      cep: '',
      endereco: '',
      bairro: '',
      cidade: '',
      uf: '',
      ddd: '',
    }
  },
  methods: {
    async consultarCep() {
      if (!this.cep || this.cep.length < 8) {
        this.limpar()
        return
      }
      const result = await axios(`https://viacep.com.br/ws/${this.cep}/json/`)
      const dados = result.data
      console.log('dados - cep:', dados)
      this.endereco = dados.logradouro
      this.bairro = dados.bairro
      this.cidade = dados.localidade
      this.uf = dados.uf
      this.ddd = dados.ddd
    },

    limpar() {
      this.endereco = ''
      this.bairro = ''
      this.cidade = ''
      this.uf = ''
      this.ddd = ''
    },
  },
}
</script>

<style lang="css" scoped></style>
