<template>
  <div class="container">
    <NuxtLink class="col-2 btn btn-secondary" to="/">Home</NuxtLink>
    <h1 class="col-10">Mostrar/Ocultar Campos</h1>

    <div class="row">
      <h2>Form1</h2>
      <form class="col-12 form-1" @submit.prevent.stop>
        <div class="input-group mb-3">
          <span class="input-group-text">Professor</span>
          <select v-model="turmaA.professorId" class="form-select">
            <option disabled hidden value="">Selecione</option>
            <option
              v-for="item in listaProfessor"
              :key="item.id"
              :value="item.id"
            >
              {{ item.name }}
            </option>
          </select>
        </div>

        <div class="input-group mb-3">
          <span class="input-group-text">Aluno</span>
          <select v-model="turmaA.alunoId" class="form-select">
            <option disabled hidden value="">Selecione</option>
            <option v-for="item in listaAluno" :key="item.id" :value="item.id">
              {{ item.aluno }}
            </option>
          </select>
        </div>
      </form>
    </div>

    <div class="row">
      <h2>Form2</h2>
      <form class="col-12 form-2" @submit.prevent.stop>
        <div class="input-group mb-3">
          <span class="input-group-text">Aluno</span>
          <select v-model="turmaB.alunoId" class="form-select">
            <option disabled hidden value="">Selecione</option>
            <option v-for="item in listaAluno" :key="item.id" :value="item.id">
              {{ item.aluno }}
            </option>
          </select>
        </div>
        <div class="input-group mb-3">
          <button
            type="submit"
            class="btn btn-primary"
            @click.prevent.stop="enviar"
          >
            Enviar
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'

const LISTA_PROFESSOR = {
  data: [
    {
      id: 1,
      name: 'Leonardo Bruno',
    },
    {
      id: 2,
      name: 'Maya Nicole',
    },
  ],
}

const LISTA_ALUNO = {
  data: [
    {
      id: 1,
      aluno: 'Aluno1',
    },
    {
      id: 2,
      aluno: 'Aluno2',
    },
  ],
}

export default {
  name: 'HideFieldTemplate',
  components: {},
  props: {},
  setup() {
    const listaProfessor = ref(LISTA_PROFESSOR.data)
    const listaAluno = ref(LISTA_ALUNO.data)
    const turmaA = ref({
      professorId: '',
      alunoId: '',
    })
    const turmaB = ref({
      professorId: '',
      alunoId: '',
    })
    const enviar = () => {
      const dadosEnviarNoAxios = {
        turmaA: turmaA.value,
        turmaB: {
          ...turmaB.value,
          professorId: turmaA.value.professorId,
        },
      }
      console.log(
        'enviar -> dadosEnviarNoAxios ',
        'font-size:12px;background-color:#b8644f;color:white;',
        dadosEnviarNoAxios
      )
    }

    return {
      listaAluno,
      listaProfessor,
      turmaA,
      turmaB,
      enviar,
    }
  },
}
</script>

<style lang="css" scoped>
.form-1 {
  border: 1px solid blue;
  padding: 20px;
}
.form-2 {
  border: 1px solid red;
  padding: 20px;
}
.resultado {
  border: 1px solid green;
  padding: 20px;
}
</style>
