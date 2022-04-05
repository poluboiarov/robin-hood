<template>
  <div class="gameboard__cell" :style="cellCoordinates">
    <div v-if="players.length > 0" class="gameboard__cell--camp">
      <PlayerStatue v-for="name in players" 
        :key="name + ' player'" 
        :name="name" 
        :size="statueSize"
        @moveStatue="moveStatue"
        @passDice="rollDice" />
    </div>
    <div v-else>{{ name }}</div>
    <Arrow v-if="destination" 
      :from="{ name: name, x: x, y: y }" 
      :to="destination" />
  </div>
</template>

<script>
import PlayerStatue from '@/components/PlayerStatue.vue';
import Arrow from '@/components/Arrow.vue';

export default {
  name: 'BoardCell',
  components: {
    PlayerStatue,
    Arrow
  },
  props: {
    name: [String, Number],
    x: {
      type: Number,
      required: true
    },
    y: {
      type: Number,
      required: true
    },
    players: {
      type: Array,
      default: []
    },
    destination: Object
  },
  computed: {
    cellCoordinates() {
      return {
        'grid-column-start': this.x, 
        'grid-row-start': this.y
      }
    },
    statueSize() {
      return 1.5 / this.players.length
    }
  },
  methods: {
    rollDice(diceData) {
      this.$emit('passDice', diceData)
    },
    moveStatue(player) {
      this.$emit('moveStatue', { 
        playerName: player.name, 
        moveFrom: this.name, 
        moveTo: parseInt(this.name + player.dice)
      })
    }
  },
}
</script>

<style lang="less">
.gameboard {
  &__cell {
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
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
  
    &--camp {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 100%;
      height: 100%;
    }
  }
}
</style>