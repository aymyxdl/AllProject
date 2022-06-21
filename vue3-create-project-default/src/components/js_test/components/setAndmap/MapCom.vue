<template>MapCom</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "MapCom",
  setup() {
    const m1 = new Map([
      ["a", 111],
      ["b", 222],
    ]);
    console.log(m1); // {"a" => 111, "b" => 222}
    m1.get("a"); // 111

    const m2 = new Map([["c", 3]]);
    const m3 = new Map(m2);
    m3.get("c"); // 3
    m3.has("c"); // true
    m3.set("d", 555);
    m3.get("d"); // 555

    // m1.set(m2)
    for (let i of m1) {
      console.log(i);
    }

    console.log(m1.keys());
    console.log(m1.values());
    console.log(m1.entries());
    
    m1.forEach((value, key) => {
      console.log(value, key);
    })

    console.log(m1.size);
    

    // ******************
    console.log('******************');
    const s1 = new Set([1,322,3,2,1,4,5,2]);
    console.log(s1);
    const values = s1.values();
    console.log(values.next());
    console.log(values.next());
    
    const values2 = m1.values();
    console.log(values2.next());
    console.log(values2.next());
    console.log(values2.next());

    console.log(s1.keys());
    console.log(s1.values());
    
    const dom1 = document.getElementsByTagName('body');
    console.log(dom1);
    console.log(Object.prototype.toString.call(dom1));
    
    
    
  },
});
</script>

<style>
</style>