<template>
  <div class="player" :style="statueSize" @click="moveStatue">
    <span class="player__statue" v-html="statueColor"></span>
  </div>
</template>

<script>
export default {
  name: 'PlayerStatue',
  props: {
    name: {
      type: String,
      required: true
    },
    size: Number
  },
  data() {
    return {
      colors: {
        red: '&#128308;',
        green: '&#128994;',
        blue: '&#128309;',
        yellow: '&#128993;',
        purple: '&#128995;',
        brown: '&#128996;',
        black: '&#9899;',
        white: '&#9898;'
      },
      dice: 0
    }
  },
  computed: {
    statueColor() {
      return this.colors[this.name]
    },
    statueSize() {
      return (this.size >= 1) ? 'font-size: 1em' : `font-size: ${this.size}em`
    }
  },
  methods: {
    rollDice() {
      let random = Math.random() * 6 + 1
      this.dice = Math.floor(random)

      this.$emit('passDice', { player: this.name, dice: this.dice })
    },
    moveStatue() {
      this.rollDice()
      this.$emit('moveStatue', { name: this.name, dice: this.dice })
    }
  },
}
</script>

<style lang="less">
.player {
  cursor: pointer;
  user-select: none;

  &__statue {
    position: relative;
    top: 0.055em;
  }
}
</style>