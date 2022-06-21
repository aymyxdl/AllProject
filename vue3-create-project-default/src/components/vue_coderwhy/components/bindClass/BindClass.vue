<template>
  BindClass
  <div :class="{active: isActive}" @click="isActive = !isActive">测试class{{ isActive }}</div>
  <div :class="getLine()" @click="isLine = !isLine">测试class2{{ isLine }}</div>

  <div>
    作业:点击哪个li标签，就标红
    <ul>
      <li
        v-for="(item, index) in arr"
        :class="{active: index === curIndex}"
        @click="curIndex = index"
        :key="index + Math.random()">
        {{item}}
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref } from 'vue';

export default defineComponent({
  name: 'BindClass',
  setup() {
    
    const isActive = ref(true);
    const isLine = ref(true);
    const curIndex = ref(0);
    const arr = reactive([1,2,3,4,5,6]);
    console.log(isActive, isLine, curIndex);
    
    
    const getLine = () => {
      // alert(isLine.value);
      // console.log({line: isLine});
      
      return {line: isLine.value}
    }
    
    return {
      isActive,
      getLine,
      isLine,
      curIndex,
      arr
    }
  }
});
</script>

<style lang="less" scoped>
  .active,
  .line {
    color: red;
  }
</style>