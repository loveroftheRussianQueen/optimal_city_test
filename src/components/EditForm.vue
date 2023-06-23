<script setup>
import { ref } from 'vue'

const props = defineProps(['value'])
const emit = defineEmits(['close, edit'])

const newValue = ref(props.value)

const editValue = () => {
  emit('edit', newValue)
  emit('close')
}
</script>

<template>
  <div class="modal">
    <form>
      <input type="text" placeholder="Change a value" v-model="newValue" />
      <button @click.prevent="editValue">Save changes</button>
      <span class="close" @click="$emit('close')">Close</span>
    </form>
  </div>
</template>

<style lang="scss" scoped>
.modal {
  position: fixed;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background-color: rgba($color: #a89f9f, $alpha: 0.6);
  z-index: 99;

  form {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    gap: 30px;
    width: 500px;
    height: 300px;
    background-color: #fff;
    border-radius: 10px;

    input {
      width: 70%;
      padding: 12px 20px;
      margin: 8px 0;
      border: 1px solid #ccc;
      border-radius: 4px;
      outline: none;
    }

    button {
      cursor: pointer;
      padding: 10px 15px;
      border-radius: 10px;
      border: 1px solid rgb(236, 233, 233);
      color: #000;
      font-size: 16px;
    }
  }

  .close {
    cursor: pointer;
    position: absolute;
    font-size: 16px;
    color: #000;
    right: 15px;
    top: 15px;
    transition: 0.3s ease-out;

    &:hover {
      color: #4e4c4c;
    }
  }
}
</style>
