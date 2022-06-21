<template>PromiseFun</template>

<script lang="ts">
import { defineComponent } from "vue";
import axios from "axios";

export default defineComponent({
  name: "PromiseFun",
  setup() {
    // 利用Promise和	async /await实现以下功能：
    // 现有一个接口https://test.com/get?id=1，
    // 需要发起id从1~200的GET方式调用200次异步请求，
    // 要求分20轮发出，前一轮全部完成后才进行下一轮，每轮同时并发请求为10次。
    const count = 200;
    const num = 20;
    const url = "https://test.com/get?id=";

    function getData(id) {
      return new Promise((resolve) => {
        console.log(url + id);
        axios.get(url + id).then(
          // eslint-disable-next-line
          response => {
            resolve();
          },
          // eslint-disable-next-line
          reason => {
            // console.log(url + id);
            resolve();
          }
        );
      });
    }

    function leep(id) {
      let p = [];
      const len = count / num;
      for (let i = 1; i <= len; i++) {
        p.push(getData(id * len + i));
      }
      return Promise.all(p);
    }

    async function start() {
      for (let i = 0; i < num; i++) {
        await leep(i);
      }
    }

    start();
  },
});
</script>

<style>
</style>