<script setup lang="ts">
import {ref} from "vue";

const todoList = ref([
  {id: 1, title: 'Learn Vue.js', details: '....'},
  {id: 2, title: 'Go shopping', details: 'buy milk'},
  {id: 3, title: 'Gym', details: '123'},
])

const selectedTodoId = ref<number | null>(null)

const onTodoTitleClick = (id: number) => {
  if (selectedTodoId.value === id) {
    selectedTodoId.value = null
  } else {
    selectedTodoId.value = id
  }
}
</script>

<template>
  <main>
    <h1>My Todos</h1>
    <ul>
      <li v-for="todo of todoList" :key="todo.id">
        <a @click="onTodoTitleClick(todo.id)">{{ todo.title }}</a>
        <div v-if="selectedTodoId === todo.id">{{ todo.details }}</div>
      </li>
    </ul>
  </main>
</template>
