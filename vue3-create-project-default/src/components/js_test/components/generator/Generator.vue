<template>Generator生成器</template>

<script lang="ts">
import axios from "axios";
import { defineComponent } from "vue";

export default defineComponent({
  name: "Generator",
  setup() {
    function* gen() {
      console.log(1);
      // yield { a: "123", b: [1, 2, 3, 4] };
      // yield true;
      yield;
      console.log(2);
      yield;
      console.log(3);
    }
    const g = gen();
    // console.log(g);
    // 只要调用了 next 方法，才会开始执行 生成器函数中的代码
    // console.log(typeof g.next().value);
    console.log(g.next());


    // 使用 generator 来部署 iterator 接口

    const obj = {
      name: 'Tom',
      age: '15',
      gender: 'male',
      [Symbol.iterator]: function * () {
        let i = 0;
        const arr = Object.values(this);
        yield arr[i++];
        yield arr[i++];
        yield arr[i++];
      }
    }

    for (let i of obj) {
      console.log(i);
    }
    
    // 不过这样有隐患：yield写死了就返回三次，如果后续添加了属性，就不能 of 出来了
    console.log('**************');

    function * asyncFunc () {
      let url = yield getNews('http://localhost:3000/posts/1');
      yield getNews(url);

      // 多两层嵌套就出问题了
      // url = yield getNews(url);
      // yield getNews(url);
    }

    function getNews(url) {
      const res = axios.get(url);
      res.then(res => {
        url = 'http://localhost:3000/comments?postId=' + res.data.postId;
        console.log(url);
        af.next(url);
      }).catch(reason => {
        console.log(reason);
        return new Promise(() => {});
      })
    }


    const af = asyncFunc();
    console.log(af.next());

    // 我感觉这东西冗余太严重了，代码极度混杂，而且多嵌套两层，那个地址参数就出问题了，更不要说返回结果的处理
    // 局限性太大了
  },
});
</script>

<style>
</style>