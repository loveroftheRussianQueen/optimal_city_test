<script setup>
import { ref } from 'vue'

import { items } from '../data/items'
import ListItem from './ListItem.vue'
import EditForm from './EditForm.vue'

const isShowModal = ref(false)

const item = ref({ name: String, value: String })

const openModal = (name, value) => {
  item.value = { name: name, value: value }
  isShowModal.value = true
}

const closeModal = () => {
  isShowModal.value = false
}

const editItem = (value) => {
  item.value.value = value
  for (let i = 0; i < items.length; i++) {
    if (items[i]['name'] == item.value.name && items[i]['value'] !== item.value.value) {
      items[i]['value'] = item.value.value
    }
  }
  return items
}
</script>

<template>
  <div class="list">
    <ListItem
      v-for="list_item in items"
      :name="list_item.name"
      :value="list_item.value"
      :key="list_item.name"
      @click="openModal(list_item.name, list_item.value)"
    />
    <EditForm
      ref="form"
      v-if="isShowModal"
      @close="closeModal"
      :value="item.value"
      @edit="editItem"
    />
  </div>
</template>

<style lang="scss" scoped>
.list {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  gap: 10px;
  padding: 20px;
  background-color: rgb(230, 228, 225);
}
</style>
