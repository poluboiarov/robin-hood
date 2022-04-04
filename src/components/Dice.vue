<template>
  <div class="dice">
    Dice: {{ getDice }} for <span :style="{'color': getPlayer, 'text-transform': 'capitalize' }">{{ getPlayer }}</span>
  </div>
</template>

<script>
export default {
  name: 'Dice',
  props: {
    player: {
      type: String,
      required: true
    },
    dice: {
      type: Number,
      required: true
    }
  },
  computed: {
    getPlayer() {
      return this.player 
    },
    getDice() {
      return this.dice
    }
  },
}
</script>

<style lang="less">
.dice {
  padding: 0.2em 0.25em;
  position: absolute;
  top: 4.625vh;
  left: 3.5vw;
  background: rgba(0, 0, 0, 0.1);
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

  &::before {
    content: '';
    display: block;
    width: 100%;
    height: 100%;
    position: absolute;
    left: 0;
    top: 0;
  }
}
</style>