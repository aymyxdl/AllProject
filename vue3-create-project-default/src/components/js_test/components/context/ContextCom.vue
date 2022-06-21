<template>
  ContextCom
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'ContextCom',
  setup() {

    console.log('global begin: ' + i);
    var i = 1;
    foo(1);
    function foo(i) {
        if (i == 4) {
            return;
        }
        console.log('foo() begin: ' + i);
        foo(i + 1); // 递归调用：在函数内部调用自己
        console.log('foo() end: ' + i);
    }
    console.log('global end: ' + i);


    // =============
    console.log('============');
    

    /*
        面试题1:
    */

    function a() {}
    // eslint-disable-next-line
    var a;
    console.log(typeof a);

    
    // =============
    console.log('============');

    /*
        面试题2:
    */
    if (!(b in window)) {
    var b = 1;
    }
    console.log(b); 

    // =============
    console.log('============');

    /*
        面试题3:
    */

    var c = 1;
    // eslint-disable-next-line
    function c(c) {
        console.log(c);
    }
    c(2); 

    
    // =============
    console.log('============');

    /*
        面试题3变形
    */

    var d = 1;
    // eslint-disable-next-line
    function d(d) {
        console.log(d);
        // eslint-disable-next-line
        var d = 3;          
    }
    d(2);  
  }
});
</script>

<style>
</style>