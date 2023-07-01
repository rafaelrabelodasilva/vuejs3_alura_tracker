<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>

    <div class="column is-three-quarter conteudo">
      <FormularioTarefa @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <MainTarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/> <!--Para cada tarefa no nosso array de tarefas queremos fazer alguma coisa-->
        <MainBox v-if="listaEstaVazia">
          <p>Você não está muito produtico hoje ☹️</p>
        </MainBox>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioTarefa from './components/FormularioTarefa.vue'
import MainTarefa from './components/MainTarefa.vue';
import ITarefa from './interfaces/ITarefa'
import MainBox from './components/MainBox.vue';

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormularioTarefa,
    MainTarefa,
    MainBox
  },
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    }
  },
  computed: {
    listaEstaVazia() : boolean { //Retorna verdadeiro ou falso
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa (tarefa:ITarefa) {
      this.tarefas.push(tarefa)
    },
    trocarTema(modoEscuroAtivo: boolean) {
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  }
});
</script>

<style>
.lista {
  padding: 1.25rem;
}
main {
  --bg-primario: #fff;
  --texto-primario: #000;
}
main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}
.conteudo {
  background-color: var(--bg-primario);
}
</style>
