<template>
  <div class="modal" v-if="show" @click.stop="hideDialog">
    <div class="content_modal" @click.stop>
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    show: {
      type: Boolean,
      required: true,
      default: false,
    },
  },

  methods: {
    hideDialog() {
      this.$emit("update:show", false);
    },
  },
};
</script>

<style scoped>
.modal {
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  position: fixed;
  display: flex;
  background-color: rgba(0, 0, 0, 0.5);
}

.content_modal {
  width: 700px;
  display: flex;
  flex-direction: column;
  margin: auto;
  background: white;
  border-radius: 15px;
  min-height: 50px;
  min-width: 50px;
  gap: 10px;
  padding: 30px;
}
</style>
