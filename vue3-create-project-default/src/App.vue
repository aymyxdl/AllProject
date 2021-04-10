<template>
  <div class="home-wrap" />
  <axios-test />
</template>

<script>

import AxiosTest from './components/axios/AxiosTest';

export default {
  name: 'App',
  components: {
    AxiosTest
  },
  setup() {

  }
}
</script>

<style lang="less">
body {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
  
  .home-wrap {
    height: 100px;
    width: 100px;
    background-color: pink;
  }
}
</style>
