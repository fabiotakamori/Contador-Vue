<template>
    <CompBox>
        <div class="columns">
            <div class="column is-7">
                <!--caso seja vazio a descricao, ele atribui o 2 Parâmetro-->
                {{tarefa.descricao || "Tarefa sem descrição"}}
            </div>
            <div class="column">
                <CompCronometro :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </CompBox>
</template>

<script lang="ts">

import ITarefa from "../interfaces/ITarefa";
import { defineComponent, PropType } from "vue";
import CompCronometro from "./Cronometro.vue"
import CompBox from "./Box.vue"

/*Componente*/
export default defineComponent({
    name: "CompTarefa",
    components:{
        CompCronometro,
        CompBox
    },
    props:{
        tarefa:{
            /*objeto do tipo ITarefa*/
            type: Object as PropType<ITarefa>,
            /*obrigatoria, não existe uma tarefa sem essa propriedade*/
            require: true
        }
    }
})
</script>

