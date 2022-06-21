<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <!--v-odel linka com nosso estado a descricao, fazer um bind-->
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?"
                v-model="descricao">
            </div>
            <div class="columns">
                <!--Quando for acionado o evento aotempo.. ele finaliza a tarefa-->
                <TempTemporizador @aoTemporizadorFinalizado="finalizarTarefa" />
            </div>
        </div>
    </div>   
</template>


<script lang="ts">
import {defineComponent } from "vue"
import TempTemporizador from "./Temporizador.vue"

export default defineComponent({
    name: "FormFormulario",
    /*emite esse evento*/
    emits: ['aoSalvarTarefa'],
    components:{
        TempTemporizador
    },
    /*metodo que retorna um estado, retornando um objeto*/
    data(){
        /*linkamos a variavel descricao do estado com o input */
        return{
            descricao: ''
        }
    },
    methods:{
        /*iremos receber o tempo decorrido, lembre se que ao ser vinalidado no emit é passado o nome do evento e a variavel, como temos
        uma igualdade acima, rebemos aqui em baixo*/
        finalizarTarefa (tempoDecorrido:number) : void{ 
            /* quando salvar tarefa, nosso form emite um evento e adiciona na lista*/
            this.$emit('aoSalvarTarefa',{
                duracaoEmSegundos: tempoDecorrido,
                descricao: this.descricao
            })
            console.log(this.descricao)
            this.descricao =''
        }
    }
})
</script>
