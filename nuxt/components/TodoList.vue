<template>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      {{ todo?.title || "タイトルなし" }}
      <button @click="$emit('edit', todo)">編集</button>
      <button @click="$emit('delete', todo)">削除</button>
    </li>
  </ul>
</template>

<script setup>
defineProps({
  todos: {
    type: Array,
    default: () => [] 
  }
})
</script>
