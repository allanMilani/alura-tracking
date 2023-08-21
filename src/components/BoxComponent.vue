<template>
  <div class="box has-text-weight-bold texto-descricao" :style="estilos">
    <slot></slot>
  </div>
</template>
<script lang="ts">
  import { defineComponent } from 'vue';

  export default defineComponent({
    name: 'BoxComponent',
    data () {
      return {
        estilos: {
          background: '#6894e6'      
        }
      }
    }
  });
</script>


<style scoped>
  .texto-descricao{
    color: var(--texto-primario);
  }
</style>