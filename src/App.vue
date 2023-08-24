
<template>
  <h1>
    Todo App
  </h1>
  <div class="todo-container">
  <TodoList />
</div>
</template>

<script setup>
import TodoList from './components/TodoList.vue'

</script>

<style>
#app {
  display: flex;
  flex-direction: column;
}

</style>