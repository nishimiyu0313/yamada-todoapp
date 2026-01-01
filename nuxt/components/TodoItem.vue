<template>
  <li class="todo-item">
    <span :class="{ completed: todo.completed }">{{ todo.title }}</span>
    <button @click="$emit('edit', todo)">編集</button>
    <button @click="$emit('delete', todo)">削除</button>
  </li>
</template>

<script setup>
defineProps({ todo: Object })
</script>

<style scoped>
.todo-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0.5rem;
  border-bottom: 1px solid #ddd;
}

.completed {
  text-decoration: line-through;
  color: gray;
}

button {
  margin-left: 0.5rem;
}
</style>
