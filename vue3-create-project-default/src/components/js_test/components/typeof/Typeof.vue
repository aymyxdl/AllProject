<template>
  Typeof
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Typeof',
  setup() {
    function Person(){}
    const p = new Person();
    console.log(p instanceof Person);
    
  }
});
</script>

<style>
</style>