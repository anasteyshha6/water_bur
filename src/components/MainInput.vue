<template>
  <div>
    <input
      @input="$emit('update:modelValue', $event.target.value)"
      :placeholder="placeholder"
      :value="modelValue"
    />
  </div>
</template>
<script>
export default {
  props: {
    modelValue: {
      type: String,
      required: true,
    },
    placeholder: {
      type: String,
      required: true,
    },
  },
};
</script>
<style scoped>
input {
  width: 200px;
  border-radius: 12px;
  background-color: white;
  border: 1px solid grey;
  padding: 12px;
  font-family: "Ral", sans-serif;
  color: black;
}
</style>
