<template>
    <div class="box has-text-weight-bold" :style="estilos">
        <slot></slot> <!--O que estiver aqui dentro do componente box será renderizado nele-->
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'MainBox',
    data() {
        return {
            estilos: {
                background: '#FAF0CA'
                //Se a propriedade é separada por algo poderia ser feito das seguintes formas
                //'background-color': '#FAF0CA'
                //'backgroundColor': '#FAF0CA'
            }
        }
    }
})
</script>