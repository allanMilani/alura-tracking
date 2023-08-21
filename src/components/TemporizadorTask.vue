<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <CronometroTask :tempoEmSegundos="tempoEmSegundos" />
    <ButtonComponent icon="fa-play" description="play" :clickFunction="iniciar" :disabled="cronometroRodando"/>
    <ButtonComponent icon="fa-stop" description="stop" :clickFunction="finalizar" :disabled="!cronometroRodando"/>
  </div>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';
  import CronometroTask from './CronometroTask.vue'
  import ButtonComponent from './ButtonComponent.vue'

  export default defineComponent({
    name: 'TemporizadorTask',
    emits: ['aoTemporizadorFinalizado'],
    components: {
      CronometroTask,
      ButtonComponent
    },
    data(){
      return {
        tempoEmSegundos: 0,
        cronometro: 0,
        cronometroRodando: false
      }
    },
    methods: {
      iniciar(){
        this.cronometroRodando = true
        this.cronometro = setInterval(() => {
          this.tempoEmSegundos += 1
        }, 1000)
      },
      finalizar(){
        this.cronometroRodando = false
        clearInterval(this.cronometro)
        this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
        this.tempoEmSegundos = 0
      }
    }
  });
</script>
