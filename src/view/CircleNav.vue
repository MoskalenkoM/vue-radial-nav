<template lang="pug">
  .nav_circle(:style="setRotate")
    item-nav(
      v-for="(item, index) in circleNav"
      :key="index"
      :bgImg="item.img"
      :xPos="50 + radius * Math.cos(index * dist) + '%'"
      :yPos="50 + radius * Math.sin(index * dist) + '%'"
      :itemTurnDeg="turnDeg"
    )
</template>

<script>
import ItemNav from "../components/ItemNav.vue";
// img
import NavImg1 from "../assets/img/1.png";
import NavImg2 from "../assets/img/2.png";
import NavImg3 from "../assets/img/3.png";
import NavImg4 from "../assets/img/4.png";

export default {
  props: {
    turnDeg: {
      type: Number,
      required: true
    }
  },
  components: {
    ItemNav
  },
  data() {
    return {
      circleNav: [
        { img: NavImg1 },
        { img: NavImg2 },
        { img: NavImg3 },
        { img: NavImg4 },
        { img: NavImg1 },
        { img: NavImg2 },
        { img: NavImg3 },
        { img: NavImg4 }
      ],
      radius: 50
    };
  },
  computed: {
    dist() {
      return 2 * Math.PI * (1 / this.circleNav.length);
    },
    setRotate() {
      return { transform: `rotate(${this.turnDeg}deg)` };
    }
  },
  beforeMount() {
    this.$emit("countNav", {
      count: this.circleNav.length
    });
  }
};
</script>

<style lang="postcss" scoped>
.nav_circle {
  height: 250px;
  width: 250px;
  margin: auto;
  position: relative;
  transition: transform 1s linear;
}
</style>
