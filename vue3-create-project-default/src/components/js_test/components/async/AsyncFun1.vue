<template>AsyncFun1</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "AsyncFun1",
  setup() {
    // 面试题

    function A() {
      return new Promise(resolve => {
        setTimeout(() => {
          resolve('AAA');
        }, 2000);
      })
    }

    
    function B(obj) {
      return new Promise(resolve => {
        setTimeout(() => {
          console.log(obj, '-----------');
          resolve('BBB');
        }, 3000);
      })
    }

    
    function C(obj) {
      // eslint-disable-next-line
      return new Promise((resolve, reject) => {
        setTimeout(() => {
          console.log(obj, '-----------');
          resolve('CCC');
          // reject('c错误');
        }, 3000);
      })
    }

    async function run() {
      try {
        const resultA = await A();
        const resultB = await B(resultA);
        const resultC = await C(resultB);
        console.log(resultC);
      } catch(e) {
        console.log(e);
      }
    }

    run();
  },
});
</script>

<style>
</style>