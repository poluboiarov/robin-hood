<template>
  <div class="arrow">
    <div></div>
  </div>
</template>

<script>
export default {
  name: 'Arrow',
  props: {
    from: {
      type: Object,
      required: true
    },
    to: {
      type: Object,
      required: true
    }
  },
}
</script>

<style lang="less">
.arrow {
  cursor: pointer;
  position: absolute;
  width: calc(75px * 2);
  height: 50px;
  left: calc(100% + 18px);

  div {
    position: relative;
    top: 20px;
    width: calc(75px * 2);
    height: 5px;
    background-color: #337AB7;
    box-shadow: 0 3px 5px rgba(0, 0, 0, .2);
    left:0;
    display: block;

    &::after {
      content: '';
      position: absolute;
      width: 25px;
      height: 5px;
      top: -7px;
      right: -4px;
      background-color: #337AB7;
      transform: rotate(45deg);
    }

    &::before {
      content: '';
      position: absolute;
      width: 25px;
      height: 5px;
      top: 7px;
      right: -4px;
      background-color: #337AB7;
      box-shadow: 0 3px 5px rgba(0, 0, 0, .2);
      transform: rotate(-45deg);
    }
  }
}
</style>