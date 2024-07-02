<template>
  <div class="point">
    <div class="circle">
      <img :src="imageSrc" :alt="imageAlt" />
    </div>
    <div class="step">
      <h1>{{ stepTitle }}</h1>
      <p>{{ stepDescription }}</p>
    </div>
  </div>
</template>
<script>
export default {
    props: {
        imageSrc: {
            type: String,
            required: true
        },
        imageAlt: {
            type: String,
            required: true
        },
        stepTitle: {
            type: String,
            required: true
        },
        stepDescription: {
            type: String,
            required: true
        }
    }
};
</script>
<style scoped></style>
