<template>
  ObjectAssign
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'ObjectAssign',
  setup() {
    let a = {
      a: {
        b: {
          c: [1,2,3,4]
        }
      }
    };
    let b = [{aa: 'aa', bb: {cc: 'ccc'}}, '222', 333];
    let c = {};
    Object.assign(c,a,b);
    console.log(c);
    c.a.b.c.push(4555);
    c[0].bb.cc = 'ddddd';
    console.log(a, b, c);

    // Object.assign 是浅拷贝
  }
});
</script>

<style>
</style>