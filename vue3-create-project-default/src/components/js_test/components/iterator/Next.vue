<template>NextCom</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "NextCom",
  setup() {
    const arr = [1, 2, 3, 4, 5, 6];
    for (let i of arr) {
      console.log(i);
    }
    console.log(arr);

    let arr1 = arr[Symbol.iterator]();
    console.log(arr1);
    console.log(arr1.next());

    // 对象本身并没有 iterator 接口，所以会报错
    /* let obj = {
      a: 'aaa',
      b: 'bbb'
    }; */
    let obj = {
      a: "aaa",
      b: "bbb",
      [Symbol.iterator]: function () {
        let i = 0;
        return {
          next: () => {
            const arr = Object.values(this);
            return {
              value: arr[i],
              done: i > arr.length,
            };
          },
        };
      },
    };
    let obj2 = obj[Symbol.iterator]();
    console.log(obj2);
    console.log(obj2.next());

    let obj3 = { name: "tom", age: 15, gender: "male" };
    Object.prototype.test = '123';
    Object.prototype.test2 = function() {
      console.log('test2');
    };

    for(let i of Object.values(obj3)) {
      console.log(i);
    }

    for(let i in obj3) {
      console.log(i);
    }
    
    Array.prototype.nnnnn = 888;
    console.log(arr);

    for(let i in arr) {
      console.log(i, '---');
    }

    console.log(Array.__proto__ === Function.prototype);
    console.log(Array.prototype.__proto__ === Object.prototype);

    
  },
});
</script>

<style>
</style>