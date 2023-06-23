<script setup>
const props = defineProps(['name', 'value'])
</script>

<template>
  <div class="list-item">
    <p>Name: {{ props.name }}</p>
    <p>Value: {{ props.value }}</p>
  </div>
</template>

<style lang="scss" scoped>
.list-item {
  cursor: pointer;
  padding: 5px 0px;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  border: 1px solid #000;
  border-radius: 40px;
  background-color: #dad5d5;
  width: 50%;
  transition: 0.2s ease-in-out;

  &:hover {
    background-color: #c5bfbf;
  }

  p {
    font-size: 20px;
    font-weight: 500;
    line-height: 38px;
  }
}
</style>
