<template>
  updatedLoop
  <button @click='change'>click array</button>
  <button @click='change2'>click obj</button>
  {{ a }}
  {{ obj }}
  <div class="wrap clearfix">
    <div class="box1"></div>
    <div class="box2"></div>
    <!-- <div class="clear">额外标签法</div> -->
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';

export default defineComponent({
  name: 'UpdatedLoop',
  setup() {
    const a = reactive([]);
    const obj = reactive({});

    const change = () => {
      a.push(1);
      console.log(a);
    }

    const change2 = () => {
      obj.a = 1;
    }
    return {
      a,
      obj,
      change,
      change2
    }
  },
  
  mounted() {
    console.log('mounted');
  },
  beforeCreate() {
    console.log('beforeCreate');
  },
  beforeUpdate() {
    console.log('beforeUpdate', this.a);
    // this.a.push(2);
  },
  updated() {
    console.log('beforeUpdate', this.a);
    // this.a.push(3);
    // this.obj.a = this.obj.a + 3;
    // this.a[0] = this.a[0] + 1;
  }
});
</script>

<style lang="less" scoped>
  .wrap {
    width: 500px;
    border: 2px solid red;
    // 第二种，父元素添加overflow，不推荐
    // overflow: hidden;

    .box1 {
      height: 100px;
      width: 500px;
      background: pink;
      // 然后给盒子设置浮动
      float: left;
    }

    .box2 {
      height: 200px;
      width: 500px;
      background: gray;
      float: left;
    }

    .clear {
      // 额外标签法：不推荐
      clear: both;
    }


    // 第三种,推荐
    // // &:after
    // &.clearfix:after{
    //   /*伪元素是行内元素 正常浏览器清除浮动方法*/
    //   content: "";
    //   display: block;
    //   height: 0;
    //   clear:both;
    //   visibility: hidden;
    // }
    // &.clearfix{
    //   *zoom: 1;
    //   /*ie6清除浮动的方式 *号只有IE6-IE7执行，其他浏览器不执行*/
    // }


    // 第四种,推荐
    &:after,
    &:before{
      content: "";
      display: table;
    }
    &:after{
      clear: both;
    }
  }
</style>