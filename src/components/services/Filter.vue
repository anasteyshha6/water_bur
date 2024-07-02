<template>
    <select id="filtred_difficulty" :value="modelValue" @change="chooseOpt">
      <option value="none" selected>Без сортировки</option>
      <option v-for="opt in options" :value="opt.value">{{ opt.name }}</option>
    </select>
</template>
<script>
export default {
  props: {
    modelValue: {
      type: String,
      required: true
    },

    options: {
      type: Array,
      required: true,
      default: () => []
    }
  },

  methods: {
    chooseOpt(event) {
      this.$emit('update:modelValue', event.target.value)
    }
  }
};
</script>
<style scoped>
select {
    width: 230px;
    border-radius: 12px;
    background-color: white;
    border: 1px solid grey;
    padding: 12px;
    font-family: "Ral", sans-serif;
    color: black;
}
</style>
