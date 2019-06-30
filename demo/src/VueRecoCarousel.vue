
<template>
  <div class="vue-reco-carousel">
    <div
      class="vue-reco-carousel-container"
      @touchmove="()=>{}"
      @touchstart.stop.prevent="touchStartEvent"
      @touchend.stop.prevent="touchEndEvent"
    >
      <div class="vue-reco-carousel-contents">
        <slot>default render html</slot>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import { setTimeout } from "timers";
export default {
  name: "VueRecoCarousel",
  props: { options: Object },
  components: {},
  data() {
    return {
      page_no: 0,
      pos: 0,
      scrollLeft: 0,
      t: 0,
      animation_id: 0
    };
  },
  computed: {
    transformPrefix() {
      return getComputedStyle(this.el).msTransform
        ? "msTransform"
        : getComputedStyle(list).mozTransform
        ? "mozTransform"
        : getComputedStyle(list).webkitTransform
        ? "webkitTransform"
        : "transform";
    }
  },
  methods: {
    touchStartEvent(e) {
      this.pos = e.touches[0].clientX;
    },
    touchEndEvent(e) {
      this.pos = this.pos - e.changedTouches[0].clientX;
      var el = e.target;
      this.scrollLeft = getComputedStyle(e.target).transformOrigin;
      while (el.className !== "vue-reco-carousel-container") {
        el = el.parentNode;
      }
      let left = 0;
      const max_page = parseInt(el.children[0].children.length / 3);
      let is_right = false;
      if (this.pos > 0) {
        if (this.page_no < max_page) this.page_no++;
        console.log("move right");
        is_right = true;
      } else {
        if (this.page_no > 0) this.page_no--;
        console.log("move left");
        is_right = false;
      }

      const animate_move = t => {
        if (this.t === 0) this.t = t;

        var cubicBezier = (A, B, C, D, t) => {
          if (t <= 0) {
            return A;
          }
          if (t >= 1) {
            return D;
          }
          const s = 1 - t;
          return (
            Math.pow(s, 3) * A +
            3 * (Math.pow(s, 2) * t) * B +
            3 * (s * Math.pow(t, 2)) * C +
            Math.pow(t, 3) * D
          );
        };
        const sorc = is_right
          ? parseInt(getComputedStyle(el).width) * (this.page_no - 1)
          : parseInt(getComputedStyle(el).width) * (this.page_no + 1);
        const dest = parseInt(getComputedStyle(el).width) * this.page_no;
        let diff = dest - sorc;
        console.log("(t - this.t)", t - this.t);
        const move_point = cubicBezier(
          sorc,
          sorc + diff * 0.15,
          sorc + diff * 0.85,
          dest,
          (t - this.t) / 200
        );

        el.scrollLeft = move_point;
        if (move_point !== dest || el.scrollLeft !== dest) {
          window.requestAnimationFrame(animate_move);
        } else {
          this.t = 0;
        }
      };

      window.requestAnimationFrame(animate_move);
      return true;
    }
  },

  mounted() {
    const container = document.querySelector(".vue-reco-carousel-container");
    console.log(getComputedStyle(container).width);
    const items = document.querySelectorAll(
      ".vue-reco-carousel-contents .vue-reco-carousel-item"
    );
    for (var i = 0; i < items.length; i++) {
      console.log(
        `${parseInt(getComputedStyle(container).width) /
          this.options.page_size}px`
      );
      items[i].style.maxWidth = `${parseInt(getComputedStyle(container).width) /
        this.options.page_size}px`;
      items[i].style.minWidth = `${parseInt(getComputedStyle(container).width) /
        this.options.page_size}px`;
    }
  },
  created() {
    window.slot = this.$slots;
    window.t = this;
    window.Vue = Vue;
  }
};
</script>

<style scoped>
.vue-reco-carousel {
  overflow: scroll;
  background: black;
  display: flex;
  flex-direction: row;
  align-items: center;
}
.vue-reco-carousel {
  background: white;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 0 auto;
  min-width: 100%;
}
.vue-reco-carousel-container {
  display: flex;
  flex-direction: row;
  overflow: auto;
  min-width: 100%;
  max-width: 100%;
}
.vue-reco-carousel-contents >>> .vue-reco-carousel-item {
  /* min-width: calc(100% / 4); */
}
.vue-reco-carousel-contents {
  display: flex;
  flex-direction: row;
  width: auto;
  /* max-width: 100%; */
}
</style>
