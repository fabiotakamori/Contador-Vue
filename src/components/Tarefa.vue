<template>
    <div class="box has-text-weigjt-bold">
        <div class="columns">
            <div class="column is-7">
                Descrição da tarefa
            </div>
            <div class="column">
                <CompCronometro tempoEmSegundos="15"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">

import { defineComponent } from "vue";
import CompCronometro from "./Cronometro.vue"

/*Componente*/
export default defineComponent({
    name: "CompTarefa",
    components:{
        CompCronometro
    }
})
</script>

<style scoped>
.box{
    background-color: #FAF0CA;
}
</style>