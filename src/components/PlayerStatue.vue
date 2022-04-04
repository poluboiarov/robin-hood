<template>
  <div class="player" :style="fontSize">
    <span class="player__statue" v-html="statue"></span>
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
      }
    }
  },
  computed: {
    statue() {
      return this.colors[this.name]
    },
    fontSize() {
      return {
        'font-size': (this.size >= 1) ? 1 : this.size + 'em'
      }
    }
  },
}
</script>

<style lang="less">
.player {
  &__statue {
    position: relative;
    top: 0.055em;
  }
}
</style>