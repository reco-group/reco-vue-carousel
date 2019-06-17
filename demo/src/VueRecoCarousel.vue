
<template>
  <div>
    <Items :items="list" :template="template" :mousewheel="wheelEvent" :wheel="wheel">
      <slot>default render html</slot>
    </Items>
  </div>
</template>

<script>
const Items = {
  props: {
    items: Array,
    template: Array,
    mousewheel: Function,
    wheel: Function
  },
  render(createElement) {
    return createElement(
      "div",
      {
        attrs: {
          class: "vue-reco-carousel"
        },
        on: {
          click: () => {
            console.log(123);
          },
          mousewheel: this.mousewheel,
          wheel: this.wheel
        }
      },
      this.template
    );
  }
};
export default {
  name: "VueRecoCarousel",
  props: { list: Array, classes: Array },
  components: {
    Items
  },
  data() {
    return {
      template: this.$slots.default,
      requestAnimationFrame: () => {},
      cancelAnimationFrame: () => {},
      movePoint: 0,
      ticking: false,
      isWheel: false,
      el: document.querySelector(".vue-reco-carousel")
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
    initFunction() {
      var lastTime = 0;
      var vendors = ["ms", "moz", "webkit", "o"];
      for (
        var x = 0;
        x < vendors.length && !window.requestAnimationFrame;
        ++x
      ) {
        this.requestAnimationFrame =
          window[vendors[x] + "RequestAnimationFrame"];
        this.cancelAnimationFrame =
          window[vendors[x] + "CancelAnimationFrame"] ||
          window[vendors[x] + "CancelRequestAnimationFrame"];
      }
      if (!this.requestAnimationFrame)
        this.requestAnimationFrame = function(callback, element) {
          var currTime = new Date().getTime();
          var timeToCall = Math.max(0, 16 - (currTime - lastTime));
          var id = window.setTimeout(function() {
            callback(currTime + timeToCall);
          }, timeToCall);
          lastTime = currTime + timeToCall;
          return id;
        };
      if (!this.cancelAnimationFrame) {
        this.cancelAnimationFrame = function(id) {
          clearTimeout(id);
        };
      }
    },
    getTransX() {
      const list = this.el;
      const transformPrefix = this.transformPrefix;
      return getComputedStyle(list)[transformPrefix];
    },
    listMoveX() {
      return parseInt(this.getTransX.split(",")[4]);
    },
    listMoveEnd() {
      const list = this.el;
      return (list.scrollWidth - list.offsetWidth) * -1;
    },
    listMoving: function(movePoint) {
      const list = this.el;
      const listMoveEnd = this.listMoveEnd();
      const transformPrefix = this.transformPrefix;
      let istMoveX = this.listMoveX();
      istMoveX -= movePoint;
      if (listMoveX > 0) {
        listMoveX = 0;
      } else if (listMoveX < listMoveEnd) {
        listMoveX = listMoveEnd;
      }
      console.log(transformPrefix, listMoveX);
      list.style[transformPrefix] = "translateX(" + listMoveX + "px)";
    },
    wheelEvent: function(e) {
      let movePoint =
        (e.type == "mousewheel" ? e.wheelDelta : e.deltaX) || e.deltaY;
      if (!this.ticking) {
        this.requestAnimationFrame(function() {
          this.listMoving(movePoint);
          this.ticking = false;
        });
      }
      this.ticking = true;
    },
    wheel: function(e) {
      console.log(e);
      this.wheelEvent(e);
      if (!this.isWheel) {
        e.target.parentNode.parentNode.removeEventListener(
          "mousewheel",
          this.wheelEvent
        );
        this.isWheel = true;
      }
    }
  },

  mounted() {},
  created() {
    this.initFunction();
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
.vue-reco-carousel >>> div {
  background: white;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 0 auto;
  min-width: 100%;
}
</style>
