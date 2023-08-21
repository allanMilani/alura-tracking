<template>
  <BoxComponent>
    <div class="columns">
      <div class="column is-7">
        {{ tarefa.descricao || 'Tarefa sem descrição' }}
      </div>
      <div class="column">
        <CronometroTask :tempoEmSegundos="tarefa.duracaoEmSegundo"/>
      </div>
    </div>
  </BoxComponent>
</template>

<script lang="ts">
  import { defineComponent, PropType } from 'vue';
  import CronometroTask from './CronometroTask.vue';
  import BoxComponent from './BoxComponent.vue';
  import ITarefa from '../interfaces/ITarefa';

  export default defineComponent({
    name: 'TarefaComponent',
    components: {
      CronometroTask,
      BoxComponent
    },
    props: {
      tarefa: {
        type: Object as PropType<ITarefa>,
        required: true
      }
    }
  })
</script>
