<template>
  <div id="app">
    <VueRecoCarousel :length="length">
      <div>
        <h1 class="test3">hello world</h1>
        <img
          class="event-banner-item-image"
          itemprop="contentURL"
          srcset="https://cdn.pixabay.com/photo/2017/09/22/21/23/usa-2777088_960_720.jpg 1x, https://cdn.pixabay.com/photo/2017/09/22/21/23/usa-2777088_1280.jpg 1.333x"
          src="https://cdn.pixabay.com/photo/2017/09/22/21/23/usa-2777088_960_720.jpg"
          alt="미국, 캘리포니아, 샌디에고, Del Mar, 비치, 고독, 바다, 사람, 걷기, 인간의, 물"
        >
      </div>
    </VueRecoCarousel>
  </div>
</template>

<script>
import VueRecoCarousel from "./VueRecoCarousel";
export default {
  name: "app",
  components: {
    VueRecoCarousel
  },
  data() {
    return {
      length: 12
    };
  }
};
</script>

<style scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.test3 {
  font-size: 50px;
}
.event-banner-item-image {
  width: 100%;
}
</style>
