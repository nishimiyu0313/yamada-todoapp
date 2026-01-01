<template>
  <div>
    <h1>TODO一覧</h1>
    <TodoForm @add="addTodo" />
    <TodoList :todos="todos" @edit="editTodo" @delete="deleteTodo" />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'
import TodoForm from '~/components/TodoForm.vue'
import TodoList from '~/components/TodoList.vue'

const todos = ref([])

onMounted(async () => {
  const res = await axios.get('http://localhost:8000/api/todos')
  todos.value = res.data
})

const addTodo = async (title) => {
  const res = await axios.post('http://localhost:8000/api/todos', { title })
  todos.value.push(res.data)
}

const editTodo = async (todo) => {
  const newTitle = prompt('新しいTODOを入力', todo.title)
  if (!newTitle) return
  const res = await axios.put(`http://localhost:8000/api/todos/${todo.id}`, { title: newTitle })
  todo.title = res.data.title
}

const deleteTodo = async (todo) => {
 
  await axios.delete(`http://localhost:8000/api/todos/${todo.id}`)
  todos.value = todos.value.filter(t => t.id !== todo.id)
}
</script>


