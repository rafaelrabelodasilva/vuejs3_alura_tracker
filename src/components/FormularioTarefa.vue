<template>
    <div class="box formulario">
        <div class="columns">
            <div
                class="column is-8"
                role="form"
                aria-label="Formulário para criação de uma nova tarefa"
            >
                <input
                type="text"
                class="input"
                placeholder="Qual tarefa você deseja iniciar?"
                v-model="descricaoTarefa"
                />
            </div>

            <div class="column">
                <MainTemporizador @aoTemporizadorFinalizado="finalizarTarefa"/> <!--ouve o evento customizado (aoTemporizadorFinalizado)-->
        </div>
        </div>


    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import MainTemporizador from "./MainTemporizador.vue";
export default defineComponent({
    name: "FormularioTarefa",
    emits: ['aoSalvarTarefa'],
    components: {
        MainTemporizador
    },
    data() {
        return {
            descricaoTarefa: ''
        }
    },
    methods: {
        finalizarTarefa(tempoDecorrido: number) : void {
            this.$emit('aoSalvarTarefa', {
                duracaoEmSegundos: tempoDecorrido,
                descricaoTarefa: this.descricaoTarefa
            })
            this.descricaoTarefa = ''
        }
    }
});
</script>

<style> 
.formulario {
    color: var(--texto-primario);
    background-color: var(--bg-primario);
}
</style>

