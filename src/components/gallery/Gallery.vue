<template>
  <section>
    <div class="gallery container" id="gallery">
      <MainTitle title="ГАЛЕРЕЯ НАШИХ РАБОТ" />
      <div class="head-opis">
        <p>
          Наша галерея позволит вам увидеть, как мы создаем надежные и
          эффективные скважины для наших клиентов.
        </p>
      </div>
    </div>
  </section>
  <Slider />
</template>
<script>
import MainTitle from "../MainTitle.vue";
import Slider from "./Slider.vue";

export default {
  components: {
    MainTitle,
    Slider,
  },
};
</script>
<style scoped></style>
