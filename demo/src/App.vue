<template>
  <div id="app">
    <VueRecoCarousel :options="options">
      <VueRecoCarouselItem v-for="(item, idx) in list" :key="idx">
        <h1 class="test3">hello world</h1>
        <h2>{{item.title}}</h2>
        <img class="event-banner-item-image" :src="item.image" />
      </VueRecoCarouselItem>
    </VueRecoCarousel>
    <pre>

      adfljsakdhasd
      fasfag
      asdf
      asdfads

      adfljsakdhasd
      fasfag
      asdf
      asdfads

      adfljsakdhasd
      fasfag
      asdf
      asdfads

      adfljsakdhasd
      fasfag
      asdf
      asdfads

      adfljsakdhasd
      fasfag
      asdf
      asdfads

      adfljsakdhasd
      fasfag
      asdf
      asdfads

      adfljsakdhasd
      fasfag
      asdf
      asdfads

      adfljsakdhasd
      fasfag
      asdf
      asdfads

      adfljsakdhasd
      fasfag
      asdf
      asdfads

      adfljsakdhasd
      fasfag
      asdf
      asdfads

      adfljsakdhasd
      fasfag
      asdf
      asdfads

      adfljsakdhasd
      fasfag
      asdf
      asdfads

      adfljsakdhasd
      fasfag
      asdf
      asdfads

      adfljsakdhasd
      fasfag
      asdf
      asdfads

      adfljsakdhasd
      fasfag
      asdf
      asdfads

      adfljsakdhasd
      fasfag
      asdf
      asdfads
    </pre>
  </div>
</template>

<script>
import VueRecoCarousel from "./VueRecoCarousel";
import VueRecoCarouselItem from "./VueRecoCarouselItem";
export default {
  name: "app",
  components: {
    VueRecoCarousel,
    VueRecoCarouselItem
  },
  data() {
    return {
      options: {
        page_size: 3
      },
      list: [
        {
          title: "title1 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/06/25/04/40/light-4297386_1280.jpg"
        },
        {
          title: "title2 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/04/11/20/14/dandelion-4120515_1280.jpg"
        },
        {
          title: "title3 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/04/29/14/50/camogli-4166255_1280.jpg"
        },
        {
          title: "title4 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/06/14/09/25/cloud-4273197_1280.png"
        },
        {
          title: "title5 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2017/06/17/18/35/background-2413081_1280.jpg"
        },
        {
          title: "title3 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/04/29/14/50/camogli-4166255_1280.jpg"
        },
        {
          title: "title4 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/06/14/09/25/cloud-4273197_1280.png"
        },
        {
          title: "title5 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2017/06/17/18/35/background-2413081_1280.jpg"
        },
        {
          title: "title3 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/04/29/14/50/camogli-4166255_1280.jpg"
        },
        {
          title: "title4 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/06/14/09/25/cloud-4273197_1280.png"
        },
        {
          title: "title5 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2017/06/17/18/35/background-2413081_1280.jpg"
        },
        {
          title: "title3 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/04/29/14/50/camogli-4166255_1280.jpg"
        },
        {
          title: "title4 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/06/14/09/25/cloud-4273197_1280.png"
        },
        {
          title: "title5 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2017/06/17/18/35/background-2413081_1280.jpg"
        },
        {
          title: "title3 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/04/29/14/50/camogli-4166255_1280.jpg"
        },
        {
          title: "title4 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/06/14/09/25/cloud-4273197_1280.png"
        },
        {
          title: "title5 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2017/06/17/18/35/background-2413081_1280.jpg"
        },
        {
          title: "title3 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/04/29/14/50/camogli-4166255_1280.jpg"
        },
        {
          title: "title4 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/06/14/09/25/cloud-4273197_1280.png"
        },
        {
          title: "title5 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2017/06/17/18/35/background-2413081_1280.jpg"
        },
        {
          title: "title3 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/04/29/14/50/camogli-4166255_1280.jpg"
        },
        {
          title: "title4 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/06/14/09/25/cloud-4273197_1280.png"
        },
        {
          title: "title5 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2017/06/17/18/35/background-2413081_1280.jpg"
        },
        {
          title: "title3 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/04/29/14/50/camogli-4166255_1280.jpg"
        },
        {
          title: "title4 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/06/14/09/25/cloud-4273197_1280.png"
        },
        {
          title: "title5 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2017/06/17/18/35/background-2413081_1280.jpg"
        },
        {
          title: "title3 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/04/29/14/50/camogli-4166255_1280.jpg"
        },
        {
          title: "title4 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/06/14/09/25/cloud-4273197_1280.png"
        },
        {
          title: "title5 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2017/06/17/18/35/background-2413081_1280.jpg"
        },
        {
          title: "title3 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/04/29/14/50/camogli-4166255_1280.jpg"
        },
        {
          title: "title4 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2019/06/14/09/25/cloud-4273197_1280.png"
        },
        {
          title: "title5 of vue reco carousel",
          image:
            "https://cdn.pixabay.com/photo/2017/06/17/18/35/background-2413081_1280.jpg"
        }
      ]
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
