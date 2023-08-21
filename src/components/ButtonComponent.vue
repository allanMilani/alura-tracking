<template>
  <button class="button" @click="clickFunction" :disabled="disabled">
    <span class="icon">
      <i v-bind:class="`fas ${icon}`"></i>
    </span>
    <span>{{ description }}</span>
  </button>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';

  export default defineComponent({
    name: 'ButtonComponent',
    props: {
      icon: {
        type: String,
        default: ''
      },
      description: {
        type: String,
        default: ''
      },
      clickFunction: {
        type: Function,
        default: undefined
      },
      disabled: Boolean
    }
  });
</script>