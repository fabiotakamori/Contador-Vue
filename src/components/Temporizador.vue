<template>
    <!--display flex com as atribuições padrões-->
    <div class="is-flex is-align-item-center is-justify-content-space-between">
        <!--Dizemos que temos uma propriedade tempoEmSegundos que é igual a tempoEmSegundos
                    passando nosso valor de tempo em seg via prop para o componente MyCronometro -->
        <MyCronometro :tempoEmSegundos="tempoEmSegundos"/>
        <button class="button" @click="iniciar" :disabled="cronometroRodando" >
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>play</span> 
        </button>
        <!--linkando o disabled com o estado, para isso usamos: o qual está linkado com cronometroRodando-->
        <button class="button" @click="finalizar" :disabled="!cronometroRodando">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
        </button>
    </div>
</template>

<script lang="ts">
import { tsMethodSignature } from "@babel/types"
import {defineComponent } from "vue"
import MyCronometro from './Cronometro.vue'

export default defineComponent({
    name: 'TempTemporizador',
    /*Emite um evento em um determinado momento*/
    emits:['aoTemporizadorFinalizado'],
    /*importamos e definimos como componente filho*/
    components:{
        MyCronometro
    },
    /*Estados que é um método, esse metodo retorna um objeto e é uma informação pertinente do componente*/
    data(){
        return{
            tempoEmSegundos:0,
            cronometro: 0,
            cronometroRodando: false

        }
    },

    /*Métodos*/
    methods:{
        iniciar(){

            this.cronometroRodando = true
            //começar a contagem em ms, 1seg = 1000ms, guardamos a referencia do cronometro
           this.cronometro = setInterval(()=>{
                this.tempoEmSegundos += 1
            },1000)
            console.log("Iniciando");
        },
        finalizar(){
            /*para de executar o intervalo*/
            this.cronometroRodando = false
            clearInterval(this.cronometro)

            /*Emitindo o evento, passando 2 parm 1 o nome do evento e 2 payload/carga de dados quem está ouvindo será capaz de receber*/
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
            this.tempoEmSegundos = 0
        }
    }
})
</script>
