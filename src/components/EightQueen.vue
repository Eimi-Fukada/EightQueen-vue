<template>
  <div>
    <h1 class="title" v-once>八皇后问题</h1>

    <div class="grid">
      <div class="row" v-for="(row, rowIndex) in grids" :key="rowIndex">
        <div
          class="cell"
          v-for="(cell, cIndex) in row"
          :key="cell.key"
          @click.stop="select(rowIndex, cIndex)"
        >
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
  methods: {
    select(rowIndex, cIndex) {
      if (this.validate(rowIndex, cIndex)) {
        this.grids[rowIndex][cIndex].ok = !this.grids[rowIndex][cIndex].ok;
      } else {
        alert("当前位置不能放置皇后");
      }
    },

    validate(rindex, cindex) {
      // 横
      for (let i = 0; i < this.grids[rindex].length; i++) {
        if (this.grids[rindex][i].ok) {
          return false;
        }
      }

      // 竖
      for (let i = 0; i < this.grids.length; i++) {
        if (this.grids[i][cindex].ok) {
          return false;
        }
      }

      // 撇
      for (let i = 0; i < this.grids[0].length; i++) {
        let y = rindex + cindex - i;
        if (y >= 0 && y < this.grids.length && this.grids[y][i].ok) {
          return false;
        }
      }

      // 捺
      for (let i = 0; i < this.grids[0].length; i++) {
        let y = rindex - cindex + i;
        if (y >= 0 && y < this.grids.length && this.grids[y][i].ok) {
          return false;
        }
      }

      return true;
    },
  },
};
</script>

<style scoped>
.grid {
  width: 400px;
  margin: 0 auto;
}
.row {
  width: 400px;
  height: 50px;
  display: flow-root;
}
.row:nth-child(2n) .cell:nth-child(2n) {
  background: #999;
}
.row:nth-child(2n) .cell:nth-child(2n - 1) {
  background: #efefef;
}
.cell {
  width: 50px;
  height: 50px;
  line-height: 50px;
  text-align: center;
  background: #999;
  float: left;
  cursor: pointer;
}
.cell:nth-child(2n) {
  background: #efefef;
}
</style>