<template>NewThisCom</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "NewThisCom",
  setup() {
    // 当new 碰到 this 同时存在return的情况

    function F() {
      this.name = "test";
      return {
        name: "666666",
      };
      // return true
      // return 123;
      // return null;
      // return 'sssss';
      // return undefined;
      // return [];
    }

    const f = new F();
    console.log(f.name);

    // 这个问题很奇妙
    // F() 里面如果没有 return ，那么 new F() 得到的是一个实例对象

    // 如果有 return，变成了一个 {}
    // 怪就怪在这里，如果有了return 返回了 {}
    // 那么没有return，按理来说，默认是返回undefined，f 也应该是 undefined啊
    // 怎么 new F() 还变成了 实例对象呢？

    // 这里查了一下，构造函数的返回值情况（构造函数的条件就是new 了，不new不算构造函数，就是普通调用）
    // 如果构造函数的返回值是 普通类型：字符串、数字、布尔、undefined、null，则不算返回值，实际返回其实例对象
    // 如果构造函数的返回值是引用类型，那么就返回这个引用类型，而不是返回实例对象

    // 这里因为 F 里面有this，可以注释掉 this 再试试
    // const ff = F();
    // console.log(ff);




    // ==================
    
    /* eslint-disable */
    function Foo() {
      getName = function () {
        alert(1);
      };
      return this;
    }
    Foo.getName = function () {
      alert(2);
    };
    Foo.prototype.getName = function () {
      alert(3);
    };
    var getName = function () {
      alert(4);
    };
    function getName() {
      alert(5);
    }

    // 这个代码不能在vue里面写，会有问题
    // Foo.getName();
    // getName();
    // Foo().getName();
    // getName();
    // new Foo.getName();
    // new Foo().getName();
    // new new Foo().getName();

  },
});
</script>

<style>
</style>