<template lang="pug">
  .wrap_nav(@wheel="setDeg")
    circle-nav(:turnDeg="newRotate" @countNav="setCountNav")
</template>

<script>
import CircleNav from "./view/CircleNav.vue";

export default {
  components: {
    CircleNav
  },
  data() {
    return {
      newRotate: 0,
      angle: 0
    };
  },
  methods: {
    setDeg(e) {
      let timer;
      if (e.wheelDelta >= 0) {
        clearTimeout(timer);
        timer = setTimeout(() => {
          this.newRotate -= this.angle;
        }, 4);
      } else {
        clearTimeout(timer);
        timer = setTimeout(() => {
          this.newRotate += this.angle;
        }, 4);
      }
    },
    setCountNav(nav) {
      this.angle = Math.floor(360 / nav.count);
    }
  }
};
</script>

<style lang="postcss" scoped>
.wrap_nav {
  display: flex;
  height: 100%;
  width: 100%;
}
</style>
