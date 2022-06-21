<template>AsyncFun</template>

<script lang="ts">
import axios from "axios";
import { defineComponent } from "vue";

export default defineComponent({
  name: "AsyncFun",
  setup() {
    /* 
    function getNews(url) {
      // 因为单纯的axios写在方法里，是无法把结果返回出去的
      let result = null;
      axios.get(url).then(
        response => {
          result = response;
          return response;
        }
      );
      return result;
    }

    const res = getNews('http://localhost:3000/posts/1');
    console.log(res);
     */

    // 所以需要axios配合promise一起使用
    function getNews(url) {
      return new Promise((resolve, reject) => {
        axios.get(url).then(
          (response) => {
            resolve(response.data);
          },
          (reason) => {
            reject(reason.data);
          }
        );
      });
    }

    async function as() {
      const result = await getNews("http://localhost:3000/posts/1");
      const res = await getNews(
        `http://localhost:3000/comments?postId=${result.postId}`
      );
      console.log(res);
    }

    as();
  },
});
</script>

<style>
</style>