<template>
  ClassCom
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'ClassCom',
  setup() {
    class Person {
      constructor() {}
    }

    class SubPerson extends Person {
      constructor() {
        super();
      }
    }

    const p2 = new SubPerson();
    console.log(p2);
    
    console.log(p2.__proto__ === SubPerson.prototype);
    console.log(p2.__proto__.__proto__ === Person.prototype);
    console.log(p2.__proto__.__proto__.__proto__ === Object.prototype);
    console.log(p2.__proto__.__proto__.__proto__.__proto__ === null);

    console.log('***********');
    
    // 其它的都能理解，唯独这个很特别 SubPerson.__proto__ === Person
    // 因为一般来说 实例的隐式原型 等于 构造函数的显示原型
    console.log(SubPerson.__proto__ === Person);
    console.log(SubPerson.prototype.__proto__ === Person.prototype);
    console.log(Person.__proto__ === Function.prototype);
    
  }
});
</script>

<style>
</style>