<template>
  <div class="grid">
    <b-container class="d-flex">
      <b-row v-for="row in ROWS" :key="row">
        <b-col v-for="column in COLUMNS" :key="column">
          <div class="cell"
               :class="getCellColor(row, column)"
               @click="setCellColor(row, column)">
          </div>
        </b-col>
      </b-row>
    </b-container>
    <b-button-group>
      <b-button variant="primary" @click="resetGrid()">Reset</b-button>
    </b-button-group>
  </div>
</template>

<script lang="ts">
import { Vue, Component, Watch } from 'vue-property-decorator';

@Component
export default class HabitHub extends Vue {
  private gridState: number[][] = [
    [0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0],
  ];

  private COLUMNS = 7;
  private ROWS = 10;
  private ZERO = 0;
  private ONE = 1;
  private TWO = 2;
  private THREE = 3;

  @Watch('gridState')
  private onGridStateChanged() {
    localStorage.setItem('gridState', JSON.stringify(this.gridState));
  }

  private mounted(): void {
    if (localStorage.gridState) {
      this.gridState = JSON.parse(localStorage.getItem('gridState') as string);
    }
  }

  private getCellColor(row: number, column: number): string {
    return this.gridState[row - 1][column - 1] === this.ZERO
      ? 'cell-zero'
      : this.gridState[row - 1][column - 1] === this.ONE
      ? 'cell-one'
      : this.gridState[row - 1][column - 1] === this.TWO
      ? 'cell-two'
      : this.gridState[row - 1][column - 1] === this.THREE
      ? 'cell-three'
      : '';
  }

  private setCellColor(row: number, column: number) {
    const newRow = this.gridState[row - 1].slice(0);
    newRow[column - 1] = (this.gridState[row - 1][column - 1] + 1) % 3;
    this.$set(this.gridState, row - 1, newRow);
  }

  private resetGrid(): void {
    this.gridState = [
      [0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0],
      [0, 0, 0, 0, 0, 0, 0],
    ];
  }
}
</script>

<style scoped>
.grid {
  padding-top: 7%;
}
.cell {
  border: 1px solid #09864e;
  border-radius: 10%;
  width: 45px;
  height: 45px;
  margin: 20%;
}
.cell-zero {
  background-color: #000000;
}
.cell-one {
  background-color: #b1e8d1;
}
.cell-two {
  background-color: #40b882;
}
.cell-three {
  background-color: #09864e;
}
</style>
