<template>
  <div class="hello">
    TESTING TESTING    
  </div>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator';

@Component
export default class HabitHub extends Vue {
  private gridState!: number[][] = [
    [0],[0],[0],[0],[0],[0],[0],[0],[0],[0],
    [0],[0],[0],[0],[0],[0],[0],[0],[0],[0],
    [0],[0],[0],[0],[0],[0],[0],[0],[0],[0],
    [0],[0],[0],[0],[0],[0],[0],[0],[0],[0],
    [0],[0],[0],[0],[0],[0],[0],[0],[0],[0],
    [0],[0],[0],[0],[0],[0],[0],[0],[0],[0],
    [0],[0],[0],[0],[0],[0],[0],[0],[0],[0],
  ];

  private const ZERO = 0;
  private const ONE = 1;
  private const TWO = 2;

}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

