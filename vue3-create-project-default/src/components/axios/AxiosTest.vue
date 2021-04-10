<template>
  使用axios进行 promise 的测试
</template>

<script>

import axios from 'axios';

export default {
  name: 'AxiosTest',
  components: {
  },
  setup() {
    let p = axios.get('http://localhost:3000/posts/1');

    p.then(
      result => {
        const data = result.data;
        console.log(data);
        // 一般寻常的做法是在这里面进行第二次promise的请求和回复处理
        // let p2 = axios.get(`http://localhost:3000/comments?postId=${data.postId}`);
        // p2.then(
        //   result => {
        //     console.log(result);
        //   }
        // );

        // 上面那样写，没有错，但是其实是横向编程，如果嵌套太多的话，代码横向层级就会很深
        // 所以，最好的方法是抛出去，在外面处理，让代码编程竖向编程
        return axios.get(`http://localhost:3000/comments?postId=${data.postId}`);
      },
      reason => {
        console.log('第一次请求失败' + reason);
        // 这里如果不返回，默认会返回一个 resovle 的promise
        // 所以为了使代码停止运行，需要返回一个 pendding状态的promise
        return new Promise(() => {});
      }
    ).then(
      // 链式调用，这里处理嵌套的第二个请求回调
      result => {
        console.log('第二次的数据', result.data);
      },
      reason => {
        console.log('第二次请求失败' + reason);
      }
    )
  }
}
</script>

<style lang="less" scoped>
</style>
