<template>
  <div class="home-wrap" />
  <!-- <axios-test /> -->
  <!-- <next-com /> -->
  <!-- <generator-com /> -->
  <!-- <class-com /> -->
  <!-- <async-fun /> -->
  <!-- <object-assign /> -->
  <!-- <deep-clone /> -->
  <!-- <typeof /> -->
  <!-- <i-i-f-e-com /> -->
  <!-- <new-this-com /> -->
  <!-- <scope-com /> -->
  <component :is="comString" />
</template>

<script>
import js_testDefault from './components/js_test/index';
import mianshiDefault from './components/mianshi/index';
import vue_coderwhyDefault from './components/vue_coderwhy/index';

import { ref } from 'vue';

export default {
  name: 'App',
  /* eslint-disable */
  components: {
    ...js_testDefault,
    ...mianshiDefault,
    ...vue_coderwhyDefault
  },
  setup() {
    let comString = ref('AxiosTest');
    // comString.value = 'NextCom';
    // comString.value = 'GeneratorCom';
    // comString.value = 'GeneratorCom';
    // comString.value = 'AsyncFun';
    // comString.value = 'ClassCom';
    // comString.value = 'ObjectAssign';
    // comString.value = 'DeepClone';
    // comString.value = 'Typeof';
    // comString.value = 'IIFECom';
    // comString.value = 'NewThisCom';
    // comString.value = 'PrototypeCom';
    // comString.value = 'ContextCom';
    // comString.value = 'ScopeCom';
    // comString.value = 'AsyncFun1';
    // comString.value = 'PromiseFun';
    // comString.value = 'MapCom';
    // comString.value = 'UpdatedLoop';
    // comString.value = 'BindClass';
    comString.value = 'BindStyle';
    return {
      comString
    }
  }
}
</script>

<style lang="less">
/* body {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
  
  .home-wrap {
    height: 100px;
    width: 100px;
    background-color: pink;
  }
} */
</style>
