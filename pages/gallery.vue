<template>
  <div class="container">
    <div class="section links">
      <Nav />
    </div>
    <div class="section details" style="overflow-x: hidden; overflow-y: visible;">
      <h1 class="title">Gallery 相片集錦</h1>
      <CoolLightBox 
        :items="images" 
        :index="index"
        @close="index = null">
      </CoolLightBox>

      <div class="images-wrapper">
        <div
          class="image"
          v-for="(image, imageIndex) in thumbs"
          :key="imageIndex"
          @click="index = imageIndex"
          :style="{ backgroundImage: 'url(' + image + ')' }"
        ></div>
      </div>
      <p/>
      <a class="button" target="_blank" rel="noopener" href="https://www.dignitymemorial.com/obituaries/silver-spring-md/chin-yu-lin-10273617/add-memory">Leave a Memory or Condolence 分享回憶和悼念</a>
    </div>
  </div>
</template>

<script>
import CoolLightBox from 'vue-cool-lightbox'
import 'vue-cool-lightbox/dist/vue-cool-lightbox.min.css'
 export default {
  components: {
    CoolLightBox,
  },

  data: function () {
    return {
      images: [],
      thumbs: [],
      index: null
    };
  },
  mounted() {
    this.importAll(require.context('~/assets/gallery/', true, /\.(png|jpe?g|svg)$/));
    this.importThumbs(require.context('~/assets/thumbs/', true, /\.(png|jpe?g|svg)$/));
  },

  methods: {
    importAll(r) {
      console.log(r)
      r.keys().forEach(key => (this.images.push(r(key))));
    },
    importThumbs(r) {
      console.log(r)
      r.keys().forEach(key => (this.thumbs.push(r(key))));
    },
  },
};
</script>

<style lang="scss">
.images-wrapper {
    margin-bottom: 20px;
    margin-right: 20px;
    display: flex;
    flex-wrap: wrap;
    width: 100%;
    @media screen and (max-width: 800px) {
      justify-content: center;
      width: calc(100% + 60px);
      margin-left: -30px;
      margin-bottom: 0px;
    }
}
.images-wrapper .image {
    cursor: pointer;
    background-position: 50%;
    background-repeat: no-repeat;
    background-size: cover;
    margin: 3px;
    width: 120px;
    height: 120px;
    @media screen and (max-width: 800px) {
      width: 105px;
      height: 105px;
    }
}
</style>
