<template>
    <MainBox >
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricaoTarefa || 'Tarefa sem descrição'}}
            </div>

            <div class="column">
                <MainCronometro :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </MainBox>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import MainCronometro from './MainCronometro.vue'
import ITarefa from '@/interfaces/ITarefa';
import MainBox from './MainBox.vue'

export default defineComponent({
    name: 'MainTarefa',
    components: {
        MainCronometro,
        MainBox
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
})
</script>