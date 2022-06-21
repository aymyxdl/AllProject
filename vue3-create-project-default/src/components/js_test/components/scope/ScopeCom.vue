<template>
  ScopeCom
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'ScopeCom',
  setup() {

    // eslint-disable-next-line
    var a = 10, b = 20;
    function fn(x) {
        var a = 100, c = 300;
        console.log('fn()', a, b, c, x);
        function bar(x) {
            var a = 1000, d = 400;
            console.log('bar()', a, b, c, d, x);
        }
        bar(100);
        bar(200);
    }
    fn(10);



    // 全局作用域
    // a = 10 , b = 20
    //    函数 fn 作用域 x = 10, a = 100, c = 300
    //         bar 作用域 x = 100, a = 1000, d = 400
    //         bar 作用域 x = 200, a = 1000, d = 400




    // fn 100 20 300 10
    // 1000 20 300 400 100
    // 1000 20 300 400 200


    // ===================
    console.log('===========');


    var xx = 10;
    function fnn() {
      console.log(xx);
    }
    
    function show(f) {
      // eslint-disable-next-line
      var xx = 20;
      f();
    }

    show(fnn);

    
    // ===================
    console.log('===========');


    var fn3 = function () {
      console.log(fn3);
    };
    fn3();

    var obj = {
      fn4: function() {
        // eslint-disable-next-line
        console.log(fn4);
      }
    };

    obj.fn4()
    
  }
});
</script>

<style>
</style>