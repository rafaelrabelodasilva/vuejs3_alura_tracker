<template>
    <section>
        <strong class="display">{{ tempoDecorrido }}</strong>
    </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'MainCronometro',
    props: { //Proriedades recebida do componente pai, que neste caso é do arquivo FormularioTarefa.vue
        tempoEmSegundos: {
            type: Number, //Qual o tipo da propriedade recebida
            default: 0 //Qual o valor padrão da propriedade
        }
    },
    computed: { //Monitora a informação e conforme ela é alterada ele reage e se atualiza
        tempoDecorrido() : string {
            return new Date(this.tempoEmSegundos * 1000).toISOString().slice(11, 19);
        }
    },
})
</script>

<style scoped>
.display {
    color: var(--texto-primario);
}
</style>