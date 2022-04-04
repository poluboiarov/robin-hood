<template>
  <div class="gameboard">
    <!-- Main cells -->
    <BoardCell v-for="(cell, index) in cells" 
      :key="index + ' cell'" 
      :number="cell.number"
      :x="cell.x" 
      :y="cell.y"
      :players="cell.players"
    />
    <!-- Armory cells -->
    <BoardCell v-for="(cell, index) in armory" 
      :key="index + ' armory cell'" 
      :number="cell.number"
      :x="cell.x" 
      :y="cell.y"
      :players="cell.players"
    />
    <!-- Forest cells -->
    <BoardCell v-for="(cell, index) in forest" 
      :key="index + ' forest cell'" 
      :number="cell.number"
      :x="cell.x" 
      :y="cell.y"
      :players="cell.players"
    />
    <!-- Castle cells -->
    <BoardCell v-for="(cell, index) in castle" 
      :key="index + ' castle cell'" 
      :number="cell.number"
      :x="cell.x" 
      :y="cell.y"
      :players="cell.players"
    />
  </div>
</template>

<script>
import BoardCell from '@/components/BoardCell.vue';

export default {
  name: 'GameBoard',
  components: {
    BoardCell,
  },
  data() {
    return {
      cells: [
        // to top
        { number: 1, x: 1, y: 12, players: ['red'] },
        { number: 2, x: 1, y: 11, players: ['brown', 'black', 'white'] },
        { number: 3, x: 1, y: 10 },
        { number: 4, x: 1, y: 9 },
        { number: 5, x: 1, y: 8 },
        { number: 6, x: 1, y: 7 },
        // to right
        { number: 7, x: 2, y: 7 },
        { number: 8, x: 3, y: 7 },
        { number: 9, x: 4, y: 7 },
        // to bottom
        { number: 10, x: 4, y: 8 },
        { number: 11, x: 4, y: 9 },
        { number: 12, x: 4, y: 10 },
        { number: 13, x: 4, y: 11 },
        { number: 14, x: 4, y: 12 },
        { number: 15, x: 4, y: 13 },
        { number: 16, x: 4, y: 14 },
        // to right
        { number: 17, x: 5, y: 14 },
        { number: 18, x: 6, y: 14 },
        { number: 19, x: 7, y: 14 },
        { number: 20, x: 8, y: 14 },
        { number: 21, x: 9, y: 14 },
        { number: 22, x: 10, y: 14 },
        { number: 23, x: 11, y: 14 },
        // to top
        { number: 24, x: 11, y: 13 },
        { number: 25, x: 11, y: 12 },
        { number: 26, x: 11, y: 11 },
        { number: 27, x: 11, y: 10 },
        { number: 28, x: 11, y: 9 },
        { number: 29, x: 11, y: 8 },
        { number: 30, x: 11, y: 7 },
        // to left
        { number: 31, x: 10, y: 7 },
        { number: 32, x: 9, y: 7 },
        { number: 33, x: 8, y: 7 },
        { number: 34, x: 7, y: 7 },
        { number: 35, x: 6, y: 7 },
        // to top
        { number: 36, x: 6, y: 6 },
        { number: 37, x: 6, y: 5 },
        { number: 38, x: 6, y: 4 },
        { number: 39, x: 6, y: 3 },
        { number: 40, x: 6, y: 2 },
        { number: 41, x: 6, y: 1 },
        // to right
        { number: 42, x: 7, y: 1 },
        { number: 43, x: 8, y: 1 },
        { number: 44, x: 9, y: 1 },
        { number: 45, x: 10, y: 1 },
        { number: 46, x: 11, y: 1 },
        { number: 47, x: 12, y: 1 },
        { number: 48, x: 13, y: 1 },
        // to bottom
        { number: 49, x: 13, y: 2 },
        { number: 50, x: 13, y: 3 },
        { number: 51, x: 13, y: 4 },
        { number: 52, x: 13, y: 5 },
        { number: 53, x: 13, y: 6 },
        { number: 54, x: 13, y: 7 },
        { number: 55, x: 13, y: 8 },
        { number: 56, x: 13, y: 9 },
        // to right
        { number: 57, x: 14, y: 9 },
        { number: 58, x: 15, y: 9 },
        { number: 59, x: 16, y: 9 },
        { number: 60, x: 17, y: 9 },
        { number: 61, x: 18, y: 9 },
        { number: 62, x: 19, y: 9 },
        // to top
        { number: 63, x: 19, y: 8 },
        { number: 64, x: 19, y: 7 },
        { number: 65, x: 19, y: 6 },
        { number: 66, x: 19, y: 5 },
        { number: 67, x: 19, y: 4 },
        { number: 68, x: 19, y: 3 },
        { number: 69, x: 19, y: 2 },
        { number: 70, x: 19, y: 1 },
      ],
      armory: [
        // to top
        { number: 1, x: 6, y: 11 },
        { number: 2, x: 6, y: 10, players: ['green'] },
        { number: 3, x: 6, y: 9 },
        // to right
        { number: 4, x: 7, y: 9 },
        { number: 5, x: 8, y: 9 },
        { number: 6, x: 9, y: 9 },
        // to bottom
        { number: 7, x: 9, y: 10 },
        { number: 8, x: 9, y: 11 },
        { number: 9, x: 9, y: 12 },
        // to left
        { number: 10, x: 8, y: 12 },
        { number: 11, x: 7, y: 12 },
        { number: 12, x: 6, y: 12 },
      ],
      forest: [
        // to top
        { number: 1, x: 14, y: 12 },
        { number: 2, x: 14, y: 11 },
        // to right
        { number: 3, x: 15, y: 11 },
        { number: 4, x: 16, y: 11 },
        { number: 5, x: 17, y: 11 },
        { number: 6, x: 18, y: 11 },
        // to bottom
        { number: 7, x: 18, y: 12 },
        { number: 8, x: 18, y: 13 },
        { number: 9, x: 18, y: 14, players: ['blue'] },
        // to left
        { number: 10, x: 17, y: 14 },
        { number: 11, x: 16, y: 14 },
        { number: 12, x: 15, y: 14 },
        { number: 13, x: 14, y: 14 },
        // to top
        { number: 14, x: 14, y: 13 }
      ],
      castle: [
        // to top
        { number: 1, x: 8, y: 5 },
        { number: 2, x: 8, y: 4 },
        { number: 3, x: 8, y: 3 },
        // to right
        { number: 4, x: 9, y: 3 },
        { number: 5, x: 10, y: 3, players: ['yellow', 'purple'] },
        // to bottom
        { number: 6, x: 10, y: 4 },
        { number: 7, x: 10, y: 5 },
        // to left
        { number: 8, x: 9, y: 5 }
      ]
    }
  },
}
</script>

<style lang="less">
@import url('https://fonts.googleapis.com/css2?family=Cabin+Sketch&display=swap');

.gameboard {
  display: grid;
  grid-template-rows: repeat(14, 1fr);
  grid-template-columns: repeat(19, 1fr);
  width: 100vw;
  height: 100vh;
  gap: 3px;
  padding: 4.625vh 3.5vw;

  @media (max-width: 1366px), (max-height: 768px) {
    gap: 2px;
  }

  @media (max-width: 768px), (max-height: 480px) {
    gap: 1px;
  }
}
</style>