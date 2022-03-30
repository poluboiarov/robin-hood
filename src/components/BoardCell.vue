<template>
  <div class="gameboard__cell" :style="styles">{{ number }}</div>
</template>

<script>
export default {
  name: 'BoardCell',
  props: {
    number: [String, Number],
    x: {
      type: Number,
      required: true
    },
    y: {
      type: Number,
      required: true
    }
  },
  computed: {
    styles() {
      return {
        'grid-column-start': this.x, 
        'grid-row-start': this.y
      }
    }
  },
}
</script>

<style lang="less">
.gameboard__cell {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: white;
  box-shadow: 0 0 0 3px saddlebrown;
  font-family: 'Cabin Sketch', cursive;
  font-size: 3.33333vh;
  color: saddlebrown;

  // desktop media aspect ration
  @media (min-aspect-ratio: 8/5) {
    font-size: 3.33333vh;
  }

  // mobile media aspect ration
  @media (max-aspect-ratio: 3/2) {
    font-size: 2.45vw;
  }

  @media (max-width: 1366px), (max-height: 768px){
    box-shadow: 0 0 0 2px saddlebrown;
  }

  @media (max-width: 768px), (max-height: 480px) {
    box-shadow: 0 0 0 1px saddlebrown;
  }
}
</style>