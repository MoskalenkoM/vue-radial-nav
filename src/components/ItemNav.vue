<template lang="pug">
  .item_nav(:style="setCoordinates")
</template>

<script>
export default {
  props: {
    xPos: {
      type: String,
      required: true
    },
    yPos: {
      type: String,
      required: true
    },
    bgImg: {
      type: String,
      required: true
    },
    itemTurnDeg: {
      type: Number,
      required: true
    }
  },
  computed: {
    setRotate() {
      return -this.itemTurnDeg;
    },
    setCoordinates() {
      return {
        left: this.xPos,
        top: this.yPos,
        "background-image": `url(${this.bgImg})`,
        transform: `translate(-50%, -50%) rotate(${this.setRotate}deg)`
      };
    }
  }
};
</script>

<style lang="postcss" scoped>
.item_nav {
  position: absolute;
  height: 80px;
  width: 80px;
  background-color: lightgrey;
  background-repeat: no-repeat;
  background-position: center;
  background-size: 50%;
  border-radius: 50%;
  transition: transform 1s linear;
  &:hover {
    background-color: grey;
  }
}
</style>
