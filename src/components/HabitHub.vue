<template>
  <div class="grid">
    <b-container class="d-flex">
      <b-row v-for="row in ROWS" :key="row">
        <b-col v-for="column in COLUMNS" :key="column">
          <div class="cell"
               :class="gridState[row - 1][column - 1] === ZERO
                      ? 'cell-zero'
                      : gridState[row - 1][column - 1] === ONE
                      ? 'cell-one'
                      : gridState[row - 1][column - 1] === TWO
                      ? 'cell-two'
                      : ''"
               @click="setCellColor(row, column)">
          </div>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator';

@Component
export default class HabitHub extends Vue {
  private gridState: number[][] = [
    [0, 1, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 2, 0, 0],
    [0, 0, 0, 1, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 1, 0],
    [0, 0, 0, 1, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0],
    [0, 0, 1, 0, 0, 0, 0],
    [0, 0, 2, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 2],
  ];

  private COLUMNS = 7;
  private ROWS = 10;
  private ZERO = 0;
  private ONE = 1;
  private TWO = 2;

  private getCellColor(row: number, column: number): string {
    return this.gridState[row - 1][column - 1] === this.ZERO
      ? 'cell-zero'
      : this.gridState[row - 1][column - 1] === this.ONE
      ? 'cell-one'
      : this.gridState[row - 1][column - 1] === this.TWO
      ? 'cell-two'
      : '';
  }

  private setCellColor(row: number, column: number) {
    console.log(this.gridState[row - 1][column - 1]);
    this.gridState[row - 1][column - 1] = (this.gridState[row - 1][column - 1] + 1) % 3;
  }

}
</script>

<style scoped>
.grid {
  padding-top: 5%;
}
.cell {
  width: 45px;
  height: 45px;
  margin: 20%;
}
.cell-zero {
  background-color: rgb(193, 222, 210);
}
.cell-one {
  background-color: #40b882;
}
.cell-two {
  background-color: #09864e;
}
</style>
