<template>
  <!-- v-once只是一次性插值，会影响到该节点上的其他数据绑定 -->
  <!-- v-html可以插入原始HTML -->
  <!-- v-的前缀就是vue的指令，v-bind可以用：替代，v-on可以用@替代 -->
  <!-- v-if,v-else-if, v-else -->
  <!-- v-show --- 这个元素始终会被渲染并保留在DOM中，只是简单的切换了display -->
  <!-- v-for :key , --- v-for的优先级高于v-if -->
  <!-- ref='xxx' this.$refs.xxx  (在模板渲染后) -->
  <!-- JSX --- 不写<template></template>, 直接在script里render(){return <div></div>} -->
  <div class="about">
    <!-- <h1 v-once>八皇后</h1> -->
    <eight-queen />
  </div>
</template>

<script>
import EightQueen from "../components/EightQueen.vue";

export default {
  name: "Home",
  components: {
    EightQueen,
  },
};
</script>

<style lang="less" scoped>
</style>
