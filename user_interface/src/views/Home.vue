<template>
  <div class="home">
    <b-jumbotron header-level="4" header="Route Maker" lead="Quickly make custom climbing routes">
    </b-jumbotron>
    <ImageUploader />
    <ModeSelector />
    <ImageViewer />
  </div>
</template>

<script>
// @ is an alias to /src
import ImageViewer from '@/components/ImageViewer.vue';
import ImageUploader from '@/components/ImageUploader.vue';
import ModeSelector from '@/components/ModeSelector.vue';
import { mapMutations } from 'vuex';

export default {
  name: 'Home',
  components: {
    ImageViewer,
    ImageUploader,
    ModeSelector,
  },
  /**
   * On device window loaded, set a window size to display the picture
   * for all the calculations
   */
  created() {
    window.onload = () => {
      this.setWindowWidth(this.calculateCanvaWindowWidth(window.innerWidth));
    };
    window.addEventListener('resize', () => {
      this.setWindowWidth(this.calculateCanvaWindowWidth(window.innerWidth));
    });
  },
  methods: {
    ...mapMutations('home', {
      setWindowWidth: 'setWindowWidth',
    }),
    calculateCanvaWindowWidth(innerWidth) {
      return Math.min(800, Math.floor((innerWidth / 10) * 9));
    },
  },
};
</script>
<style scoped>
.home {
  margin: 0 !important;
}
</style>
