<template>
  <div class="grid">
    <b-container fluid>
      <b-row class="text-center" v-for="row in ROWS" :key="row">
        <b-col v-for="column in COLUMNS" :key="column">
          <div class="cell" :class="getCellColor(row, column)"></div>
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
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 2, 0, 0],
    [0, 0, 0, 1, 0, 0, 0, 2, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 1, 0, 1, 0, 0],
    [0, 0, 0, 1, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
  ];

  private COLUMNS = 10;
  private ROWS = 7;
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
}
</script>

<style scoped>
.grid {
  padding-top: 25%;
}
.cell {
  width: 25px;
  height: 25px;
  margin: 5%;
}
.cell-zero {
  background-color: #42b983;
}
.cell-one {
  background-color: #f1c40f;
}
.cell-two {
  background-color: #e74c3c;
}
</style>
