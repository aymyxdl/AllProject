<template>
  PrototypeCom
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'PrototypeCom',
  setup() {
    function Person(){}
    const p = new Person();
    console.log(p.__proto__ === Person.prototype);
    console.log(p.__proto__.__proto__ === Object.prototype);
    console.log(p.__proto__.__proto__.__proto__ === null);

    console.log('*********');

    console.log(Person.__proto__ === Function.prototype);
    console.log(Person.__proto__.__proto__ === Object.prototype);

    console.log('*********');

    console.log(Function.__proto__ === Function.prototype);
    
    console.log('===========');
    console.log(Person.toString());
    console.log(Object.prototype.toString(Person), 'Person');
    console.log(Object.prototype.toString(Date), 'Date');

    console.log('********');

    console.log(Object instanceof Function);  
    console.log(Object instanceof Object);    
    console.log(Function instanceof Function);

    console.log('********');

    console.log(p.constructor === Person);
    console.log(p.constructor.prototype === p.__proto__);
    
    
    console.log('面试题*********');


    /*
        测试题1
    */

    function A () {}

    A.prototype.n = 1;

    var b = new A();

    A.prototype = {
        n: 2,
        m: 3,
    };

    var c = new A();
    console.log(b.n, b.m, c.n, c.m);
    

    /*
        测试题2
    */

    function F () {}
    Object.prototype.a = function () {
        console.log('a()');
    };
    Function.prototype.b = function () {
        console.log('b()');
    };

    var f = new F();
    f.a();
    f.b();
    F.a();
    F.b();

  }
});
</script>

<style>
</style>