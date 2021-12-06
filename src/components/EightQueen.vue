<template>
  <div>
    <h1 class="title" v-once>八皇后问题</h1>

    <div class="grid">
      <div class="row" v-for="(row, rowIndex) in grids" :key="rowIndex">
        <div class="cell" v-for="cell in row" :key="cell.key">
          <div v-if="cell.ok">Q</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
const grids = new Array(8).fill(1).map((_, r) => {
  return new Array(8).fill(1).map((_, c) => {
    return {
      key: `key-${r * 8 + c}`,
      ok: false,
    };
  });
});

export default {
  name: "EightQueen",
  data() {
    return {
      grids,
    };
  },
};
</script>

<style lang="less" scoped>
</style>