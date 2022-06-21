<template>
  <!--tudo dentro do main, conteudo da pagina,coluns= colunas, is-gapless = sem espaçamento, is-multiline=multiplas linhas -->
  <main class="columns is-gapless is-multiline modo-escuro">
    <!--um quarto do tamanho da coluna-->
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <!--tres quarto-->
    <div class="column is-three-quarter conteudo">
      <!--quando clicar irá executar o evento com @-->
      <FormFormulario @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <!--fazemos interacao, normamente usamos indice retornado do banco no keu-->
        <CompTarefa v-for="(tarefa,index) in tarefas" :key="index" :tarefa="tarefa"/>
        <!--Usando v-if para verificar conficional da variavel-->
        <CompBox v-if="listaEstaVazia">
          Você não está muito produtivo hoje :(
        </CompBox>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormFormulario from './components/Formulario.vue';
import CompTarefa from "./components/Tarefa.vue"
import ITarefa from "./interfaces/ITarefa"
import CompBox from "./components/Box.vue"

export default defineComponent({
    name: "App",
    components: { 
      BarraLateral,
      FormFormulario,
      CompTarefa,
      CompBox
      
    },
    /*Estado do componente, que retorna um objeto e queremos lista de tarefas*/
    data(){
      return {
        tarefas: [] as ITarefa[]
      }
    },
    computed:{
      /*retorna true ou false caso esteja vazio, onde usaremos acima*/
      listaEstaVazia() : boolean{
        return this.tarefas.length === 0
      }
    },
    methods:{
      /*recebe ITarefa por parâmetro*/
      salvarTarefa (tarefa: ITarefa){
        /**/
        this.tarefas.push(tarefa)
      }
    }
});
</script>

<style>
  .lista{
    padding: 1.25 rem;
  }
  main{
    --bg-primario: #fff;
    --texto-primario:#000; 
  }
  main.modo-escuro{
    --bg-primario:#2b2d42;
    --texto-primario: #ddd;
  }
  .conteudo{
    background-color: var(--bg-primario);
  }

</style>