<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <MainCronometro :tempoEmSegundos="tempoEmSegundos" />

    <button class="button" @click="iniciar" :disabled="cronometroRodando">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="finalizar" :disabled="!cronometroRodando">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import MainCronometro from "./MainCronometro.vue";
export default defineComponent({
    name: "MainTemporizador", //Cria eventos utilizados na comunicação entre componentes
    emits: ['aoTemporizadorFinalizado'],
    components: {
        MainCronometro
    },
    data() { //Método que define o estado atual do componente
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false
        }
    },
    methods: { //Funções que esse componente é capaz de executar
        iniciar() {
            this.cronometroRodando = true
            this.cronometro = setInterval(() => {//Funcionalidade do javaScript que recebe 2 parâmetros
                this.tempoEmSegundos += 1//O primeiro parâmetro é o que queremos fazer
            }, 1000) //Segundo parâmetro é o intervalo de tempo que precisa ser calculado antes de iniciar novamente em milisegundos
            console.log('Iniciando');
        },
        finalizar() {
            this.cronometroRodando = false
            clearInterval(this.cronometro) //Quando o usuário clicar em stop ele vai parar de executar o contador
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
            this.tempoEmSegundos = 0
        }
    }
});
</script>