<template>DeepClone</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "DeepClone",
  setup() {
    function getType(obj) {
      return Object.prototype.toString.call(obj);
    }

    const t1 = {
      a: 1,
      b: 2,
      c: { aa: "aa", bb: [3, 4, 6, { aaa: 123, bbb: false }] },
    };
    

    // console.log(getType([t1]));
    function clone(obj) {
      const targetType = getType(obj);
      if (targetType !== "[object Object]" && targetType !== "[object Array]")
        return obj;
      let temp = null;
      if (targetType === "[object Object]") {
        temp = {};
      } else {
        temp = [];
      }
      for (let i in obj) {
        // webpack打包是严格模式，不能使用arguments.callee
        // temp[i] = arguments.callee(obj[i]);
        temp[i] = clone(obj[i]);
      }
      return temp;
    }

    let t2 = clone(t1);
    t2.a = "a";
    t2.c.aa = true;
    t2.c.bb[2] = undefined;
    console.log(t1, t2);
  },
});
</script>

<style>
</style>