<template>
  IIFECom
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'IIFECom',
  setup() {
    // IIFE 立即执行函数
    (function () {
        var a = 1;
        function test () {
            console.log(++a);
        }
        window.$ = function () {    // 向外暴露一个函数
            return {
                test: test
            }
        }
    })()
    

    // console.log(window.$().test());    // 2
    // console.log(window.$().test());    // 3
    // console.log(window.$().test());    // 4
    // console.log(window.a);      // 4
    window.$().test();
    window.$().test();
    window.$().test();
  }
});
</script>

<style>
</style>