<template>
  <main>
    <div class="main_block container">
      <MainHead />
      <Application />
    </div>
  </main>
</template>
<script>
import MainHead from "./MainHead.vue";
import Application from "./Application.vue";

export default {
  components: {
    MainHead,
    Application,
  },
};
</script>
<style scoped></style>
