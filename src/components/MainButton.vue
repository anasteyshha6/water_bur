<template>
  <button>
    <slot></slot>
  </button>
</template>

<script>
export default {};
</script>

<style scoped>
button {
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 12px;
  padding: 15px 50px;
  margin: 28px 0;
  background: linear-gradient(to left, #0090e5 50%, #6bc9ff 100%, #00a1fe 100%);
  background-size: 200%;
  font-family: "Ral", sans-serif;
  font-weight: 400;
  color: white;
  font-size: 1rem;
  transition: 0.3s;
  cursor: pointer;
}

button:hover {
  background-position: right;
}
</style>
