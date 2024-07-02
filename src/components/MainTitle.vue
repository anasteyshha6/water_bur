<template>
  <div class="head_center">
    <h1>{{ title }}</h1>
  </div>
</template>
<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
    },
  },
};
</script>
<style scoped>
.head_center {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  text-align: center;
}

.head_center h1 {
  font-family: "Gol", sans-serif;
  font-size: clamp(1.5rem, 1.4rem + 0.5vw, 2rem);
  font-weight: 700;
  color: #01588b;
}
</style>
