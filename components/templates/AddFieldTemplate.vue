<template>
  <div class="container">
    <NuxtLink class="col-2 btn btn-secondary" to="/">Home</NuxtLink>
    <h1 class="col-10">Adicionar Campo</h1>
    <hr />

    <div>tamanho: {{ tamanho }}</div>
    <div>listaNotas: {{ listaNotas }}</div>
    <div>listaEnvio: {{ listaEnvio }}</div>
    <button class="btn btn-primary" @click="enviar">Enviar</button>
    <hr />

    <div v-for="(item, index) in listaNotas" :key="index">
      <div class="mb-3">
        <label class="form-label">Nota Fiscal</label>
        <input
          v-model="listaNotas[index]"
          class="form-control"
          type="text"
          placeholder="Nota Fiscal"
          :maxLength="tamanho"
        />
      </div>
      <button class="btn btn-primary" @click="adicionar">+</button>
      <button class="btn btn-warning" @click="remover(index)">-</button>
    </div>
  </div>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'AddFieldTemplate',
  components: {},
  props: {},
  data() {
    return {
      listaNotas: [''],
      tamanho: 5,
    }
  },
  computed: {
    ultimoIndexDoArray() {
      return this.listaNotas.length - 1
    },
    listaEnvio() {
      return this.listaNotas.filter((elemento) => elemento !== '')
    },
  },
  watch: {
    listaNotas: {
      handler() {
        if (this.listaNotas[this.ultimoIndexDoArray].length === this.tamanho) {
          this.adicionar()
        }
      },
      deep: true,
    },
  },
  methods: {
    adicionar() {
      this.listaNotas.push('')
    },
    remover(index) {
      if (this.listaNotas.length === 1) {
        return
      }
      this.listaNotas = this.listaNotas.filter((_, i) => i !== index)
    },
    enviar() {
      if (!this.validarTamanhos()) {
        alert(`Existem elementos com tamanho menor que: ${this.tamanho}`)
        return
      }
      alert('Enviado com sucesso!')
    },
    validarTamanhos() {
      return this.listaEnvio.every((element) => element.length === this.tamanho)
    },
  },
})
</script>

<style lang="css" scoped></style>
