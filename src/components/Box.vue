<template>
    <!--Outro método de atribuir css é usando a propriedade style passando um objeto -->
    <div class="box has-text-weight-bold" :style="estilos">
        <!--Usamos slot para dizer que tudo que está dentro da div box has .. será renderizado dentro do slot-->
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
    name:"CompBox",
    data () {
        return{
            estilos: {
                background: '#FAF0CA'
                /*podemos passar backgorund-color de duas forma, com aspas ou com camelcase(brackgroundColor)*/
            }
        }
    }
})
</script>

