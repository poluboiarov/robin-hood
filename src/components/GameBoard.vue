<template>
  <div class="gameboard">
    <!-- Main cells -->
    <BoardCell v-for="(cell, index) in getCells" 
      :key="index + ' cell'" 
      :name="cell.name"
      :x="cell.x" 
      :y="cell.y"
      :players="cell.players"
      @moveStatue="movePlayer"
    />
    <!-- Armory cells -->
    <BoardCell v-for="(cell, index) in getArmory" 
      :key="index + ' armory cell'" 
      :name="cell.name"
      :x="cell.x" 
      :y="cell.y"
      :players="cell.players"
      @moveStatue="movePlayer"
    />
    <!-- Forest cells -->
    <BoardCell v-for="(cell, index) in getForest" 
      :key="index + ' forest cell'" 
      :name="cell.name"
      :x="cell.x" 
      :y="cell.y"
      :players="cell.players"
      @moveStatue="movePlayer"
    />
    <!-- Castle cells -->
    <BoardCell v-for="(cell, index) in getCastle" 
      :key="index + ' castle cell'" 
      :name="cell.name"
      :x="cell.x" 
      :y="cell.y"
      :players="cell.players"
      @moveStatue="movePlayer"
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
        { name: 'Start', x: 1, y: 13 },
        { name: 1, x: 1, y: 12 },
        { name: 2, x: 1, y: 11 },
        { name: 3, x: 1, y: 10 },
        { name: 4, x: 1, y: 9 },
        { name: 5, x: 1, y: 8 },
        { name: 6, x: 1, y: 7 },
        // to right
        { name: 7, x: 2, y: 7 },
        { name: 8, x: 3, y: 7 },
        { name: 9, x: 4, y: 7 },
        // to bottom
        { name: 10, x: 4, y: 8 },
        { name: 11, x: 4, y: 9 },
        { name: 12, x: 4, y: 10 },
        { name: 13, x: 4, y: 11 },
        { name: 14, x: 4, y: 12 },
        { name: 15, x: 4, y: 13 },
        { name: 16, x: 4, y: 14 },
        // to right
        { name: 17, x: 5, y: 14 },
        { name: 18, x: 6, y: 14 },
        { name: 19, x: 7, y: 14 },
        { name: 20, x: 8, y: 14 },
        { name: 21, x: 9, y: 14 },
        { name: 22, x: 10, y: 14 },
        { name: 23, x: 11, y: 14 },
        // to top
        { name: 24, x: 11, y: 13 },
        { name: 25, x: 11, y: 12 },
        { name: 26, x: 11, y: 11 },
        { name: 27, x: 11, y: 10 },
        { name: 28, x: 11, y: 9 },
        { name: 29, x: 11, y: 8 },
        { name: 30, x: 11, y: 7 },
        // to left
        { name: 31, x: 10, y: 7 },
        { name: 32, x: 9, y: 7 },
        { name: 33, x: 8, y: 7 },
        { name: 34, x: 7, y: 7 },
        { name: 35, x: 6, y: 7 },
        // to top
        { name: 36, x: 6, y: 6 },
        { name: 37, x: 6, y: 5 },
        { name: 38, x: 6, y: 4 },
        { name: 39, x: 6, y: 3 },
        { name: 40, x: 6, y: 2 },
        { name: 41, x: 6, y: 1 },
        // to right
        { name: 42, x: 7, y: 1 },
        { name: 43, x: 8, y: 1 },
        { name: 44, x: 9, y: 1 },
        { name: 45, x: 10, y: 1 },
        { name: 46, x: 11, y: 1 },
        { name: 47, x: 12, y: 1 },
        { name: 48, x: 13, y: 1 },
        // to bottom
        { name: 49, x: 13, y: 2 },
        { name: 50, x: 13, y: 3 },
        { name: 51, x: 13, y: 4 },
        { name: 52, x: 13, y: 5 },
        { name: 53, x: 13, y: 6 },
        { name: 54, x: 13, y: 7 },
        { name: 55, x: 13, y: 8 },
        { name: 56, x: 13, y: 9 },
        // to right
        { name: 57, x: 14, y: 9 },
        { name: 58, x: 15, y: 9 },
        { name: 59, x: 16, y: 9 },
        { name: 60, x: 17, y: 9 },
        { name: 61, x: 18, y: 9 },
        { name: 62, x: 19, y: 9 },
        // to top
        { name: 63, x: 19, y: 8 },
        { name: 64, x: 19, y: 7 },
        { name: 65, x: 19, y: 6 },
        { name: 66, x: 19, y: 5 },
        { name: 67, x: 19, y: 4 },
        { name: 68, x: 19, y: 3 },
        { name: 69, x: 19, y: 2 },
        { name: 70, x: 19, y: 1 },
      ],
      armory: [
        // to top
        { name: 1, x: 6, y: 11 },
        { name: 2, x: 6, y: 10 },
        { name: 3, x: 6, y: 9 },
        // to right
        { name: 4, x: 7, y: 9 },
        { name: 5, x: 8, y: 9 },
        { name: 6, x: 9, y: 9 },
        // to bottom
        { name: 7, x: 9, y: 10 },
        { name: 8, x: 9, y: 11 },
        { name: 9, x: 9, y: 12 },
        // to left
        { name: 10, x: 8, y: 12 },
        { name: 11, x: 7, y: 12 },
        { name: 12, x: 6, y: 12 },
      ],
      forest: [
        // to top
        { name: 1, x: 14, y: 12 },
        { name: 2, x: 14, y: 11 },
        // to right
        { name: 3, x: 15, y: 11 },
        { name: 4, x: 16, y: 11 },
        { name: 5, x: 17, y: 11 },
        { name: 6, x: 18, y: 11 },
        // to bottom
        { name: 7, x: 18, y: 12 },
        { name: 8, x: 18, y: 13 },
        { name: 9, x: 18, y: 14 },
        // to left
        { name: 10, x: 17, y: 14 },
        { name: 11, x: 16, y: 14 },
        { name: 12, x: 15, y: 14 },
        { name: 13, x: 14, y: 14 },
        // to top
        { name: 14, x: 14, y: 13 }
      ],
      castle: [
        // to top
        { name: 1, x: 8, y: 5 },
        { name: 2, x: 8, y: 4 },
        { name: 3, x: 8, y: 3 },
        // to right
        { name: 4, x: 9, y: 3 },
        { name: 5, x: 10, y: 3 },
        // to bottom
        { name: 6, x: 10, y: 4 },
        { name: 7, x: 10, y: 5 },
        // to left
        { name: 8, x: 9, y: 5 }
      ]
    }
  },
  computed: {
    getCells() {
      return this.cells 
    },
    getArmory() {
      return this.armory
    },
    getForest() {
      return this.forest
    },
    getCastle() {
      return this.castle
    }
  },
  beforeMount() {
    this.cells.forEach((cell) => { cell.players = [] })
    this.cells[0].players = ['red', 'green', 'blue']
  },
  methods: {
    movePlayer(moveData) {
      let fromCell = this.cells.find((cell) => cell.name === moveData.moveFrom)
      let toCell = this.cells.find((cell) => cell.name === moveData.moveTo)
      let playerIndex = fromCell.players.indexOf(moveData.playerName)

      this.removeStatue(fromCell, playerIndex)
      this.addStatue(toCell, moveData.playerName)
    },
    removeStatue(cell, player) {
      cell.players.splice(player, 1)
    },
    addStatue(cell, player) {
      cell.players.push(player)
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