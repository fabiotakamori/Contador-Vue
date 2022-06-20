<template>
         <section>
            <strong>
                <!--podemos chamar de dessa forma, o vue sabe que é uma propriedade do estado do componente porem calculado-->
                {{ tempoDecorrido }}
            </strong>
        </section>
</template>

<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
    name:"MyCronometro",
    /*iremos criar uma outra propriedade, tudo que iremos receber do componente pai*/
    props: {
        /*aqui que recebemos o tempoEmSegundos via Cronometro*/
        tempoEmSegundos:{
            /*Numero e por default o valor é zero*/
            type: Number,
            default: 0
        }
    },
    /*Informação computada, monitora uma informação, conforme a informação é alterada, ele vai reagir e sera alterada
    SEMPRE que for inserir tipo, utilize ts la na tg script, o qual indicasa type script*/
    computed:{
        tempoDecorrido():string {
            /*Construtor do a data, tem o metodo que recebe em ms que representa uma data, multiplicamos 1000 para transforma em seg */
            /*11,8 pega apenas os campos de hora */
            return new Date(this.tempoEmSegundos*1000).toISOString().substr(11,8)
        }
    },
})


</script>