<template>
  BindStyle
  <h2 :style="{fontSize: finalSize}">你好啊</h2>

  宽度固定，普通js开发 高度不用设置，会自适应
  小程序不行，固定值，坑



  瀑布流的两种方式：
  <div class="img-container">
    <div class="item">
      <img src="https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3228549874,2173006364&fm=26&gp=0.jpg">
      <img src="https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=1838988081,2167427448&fm=26&gp=0.jpg">
    </div>
    <div class="item">
      <img src="https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=3225163326,3627210682&fm=26&gp=0.jpg">
      <img src="https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=3365503159,1655500687&fm=26&gp=0.jpg">
    </div>
  </div>

  
  <div class="img-container2">
    <img src="https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3228549874,2173006364&fm=26&gp=0.jpg">
    <img src="https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=1838988081,2167427448&fm=26&gp=0.jpg">
    <img src="https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=3225163326,3627210682&fm=26&gp=0.jpg">
    <img src="https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=3365503159,1655500687&fm=26&gp=0.jpg">
    <img src="https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=1838988081,2167427448&fm=26&gp=0.jpg">
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'BindStyle',
  setup() {
    const finalSize = ref('70px');
    return {
      finalSize
    }
  }
});
</script>

<style lang="less" scoped>

  .img-container {
    width: 600px;
    height: 1000px;
    // background-color: red;
    display: flex;
    flex-direction: row;

    .item {
      flex: 1;
      
      img {
        width: 100%;
      }
    }
  }

  .img-container2 {
    width: 600px;
    -moz-column-count: 2;
    -webkit-column-count: 2;
    column-count: 2;

    -moz-column-gap: 10rpx;
    -webkit-column-gap: 10rpx;
    column-gap: 10rpx;

    img {
      width: 100%;
    }
  }

</style>