<template>
  <div>
    <input v-model="newTitle" placeholder="TODOを入力" />
    <button @click="submit">追加</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const emit = defineEmits(['add'])
const newTitle = ref('')

const submit = () => {
  const title = newTitle.value.trim()
  if (!title) return
  emit('add', title)
  newTitle.value = ''
}
</script>
