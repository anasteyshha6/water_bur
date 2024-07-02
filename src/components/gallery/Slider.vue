<template>
  <div class="slider">
    <img
      v-for="(image, index) in images"
      :key="index"
      class="slider-img"
      :class="{ active: index === currentIndex }"
      :src="image.src"
      :alt="image.alt"
    />
    <div @click="prevSlide" class="prev controls">
      <img src="/imgs/arrow_l.svg" alt="previous" />
    </div>
    <div @click="nextSlide" class="next controls">
      <img src="/imgs/arrow_r.svg" alt="next" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      images: [
        { src: "/imgs/g1.png", alt: "img1" },
        { src: "/imgs/g2.png", alt: "img2" },
        { src: "/imgs/g3.png", alt: "img3" },
        { src: "/imgs/g4.png", alt: "img4" },
        { src: "/imgs/g5.png", alt: "img5" },
        { src: "/imgs/g6.png", alt: "img6" },
      ],
      currentIndex: 0,
    };
  },

  methods: {
    prevSlide() {
      console.log("Previous Slide", this.currentIndex);
      this.currentIndex =
        (this.currentIndex + this.images.length - 1) % this.images.length;
    },

    nextSlide() {
      console.log("Next Slide", this.currentIndex);
      this.currentIndex = (this.currentIndex + 1) % this.images.length;
    },
  },
};
</script>
<style scoped>
</style>
