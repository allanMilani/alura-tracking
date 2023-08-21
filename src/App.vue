<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLaretal @aoTemaAlterado="trocarTema" />
    </div>
    <div class="column is-three-quarter conteudo">
      <FormularioTrack @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <TarefaComponent v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
        <BoxComponent v-if="listEstaVazia">Você não está muito produtivo hoje :( </BoxComponent>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLaretal from './components/BarraLaretal.vue';
import FormularioTrack from './components/FormularioTrack.vue';
import TarefaComponent from './components/TarefaComponent.vue';
import BoxComponent from './components/BoxComponent.vue';
import ITarefa from './interfaces/ITarefa'

export default defineComponent({
  name: 'App',
  components: {
    BarraLaretal,
    FormularioTrack,
    TarefaComponent,
    BoxComponent
  },
  data(){
    return {
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    }
  },
  computed: {
    listEstaVazia() : boolean{
      return this.tarefas.length <= 0
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa){
      this.tarefas.push(tarefa);
    },
    trocarTema(modeEscuroAtivo: boolean){
      this.modoEscuroAtivo = modeEscuroAtivo

    }
  }
});
</script>

<style>
  .lista{
    padding: 1.5rem;
  }
  
  main {
    --bg-primario: #fff;
    --texto-primario: #000;
  }

  main.modo-escuro{
    --bg-primario: #2b2d42;
    --texto-primario: #ddd;
  }

  .conteudo{
    background: var(--bg-primario);
  }
</style>
