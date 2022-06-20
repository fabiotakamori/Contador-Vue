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
    </header>
</template>

<script lang="ts">
/*Definimos e exportamos o componente de nome BarraLateral*/
import {defineComponent } from "vue"

export default defineComponent({
    name: "BarraLateral"
})
</script>

<style scoped>
header{
    background: #0d3b66;
    width: 100%;
    height: 100vh;
    padding: 1rem;
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