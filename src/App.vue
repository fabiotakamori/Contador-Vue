<template>
  <!--tudo dentro do main, conteudo da pagina,coluns= colunas, is-gapless = sem espaçamento, is-multiline=multiplas linhas -->
  <main class="columns is-gapless is-multiline">
    <!--um quarto do tamanho da coluna-->
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <!--tres quarto-->
    <div class="column is-three-quarter">
      <FormFormulario />
      <div class="lista">
        <CompTarefa />
        <CompTarefa />
        <CompTarefa />
        <CompTarefa />
        <CompTarefa />
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormFormulario from './components/Formulario.vue';
import CompTarefa from "./components/Tarefa.vue"

export default defineComponent({
    name: "App",
    components: { 
      BarraLateral,
      FormFormulario,
      CompTarefa
    }
});
</script>

<style>
  .lista{
    padding: 1.25 rem;
  }
  
</style>