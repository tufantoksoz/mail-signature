<template>
  <Signature></Signature>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Signature from './components/signature.vue';

export default defineComponent({
  name: 'App',
  components: {
    Signature,
  },
});
</script>
