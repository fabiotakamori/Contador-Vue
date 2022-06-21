<!--Componente vue e divido sempre em 3 porçoes
1-html
2-js (ts= typescript)
3-css
-->
<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt=""/>
        </h1>
        <button class="button" @click="alterarTema">
            {{textoBotao}}
        </button>
    </header>
</template>

<script lang="ts">
/*Definimos e exportamos o componente de nome BarraLateral*/
import {defineComponent } from "vue"

export default defineComponent({
    name: "BarraLateral",
    emits: ['aoTemaAlterado'],
    data (){
        return{
            modoEscutoAtivo: true
        }
    },
    computed: {
        textoBotao(){
            if(this.modoEscutoAtivo){
               
                 return "Ativar modo escuro"
            }
            return "Desativar modo escurto"
            
        }
    },
    methods:{
        alterarTema(){
            this.modoEscutoAtivo = !this.modoEscutoAtivo
            this.$emit('aoTemaAlterado', !this.modoEscutoAtivo)
        }
    }
})
</script>

<style scoped>
header{
    background: #0d3b66;
    width: 100%;
    height: 100vh;
    padding: 1rem;
    text-align: center;
}
header img{
    height: 150px;
    width: 100%;
}
/*mobile*/
@media only screen and (max-width:768px){
    header{
        padding: 2.5 rem;
        height: auto;
    }
    
}
</style>