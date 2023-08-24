<template>
  <div class="container">
    <h2>Todo List</h2>
    <input v-model="searchTerm" class="todo-search" placeholder="Filter" />
    <input type="checkbox" v-model="isGridLayout" />
    <label>Grid Layout</label>
    <div>
    <input v-model="newTodo" />
    <button @click="addTodo">Add Todo</button>
  </div>
  <div v-if="isLoading">Loading...</div>

    <div v-else class="layout" :class="{'grid': isGridLayout}">
      <TodoItem v-for="todo in filteredTodos" :key="todo.id" :toggle="toggle" :deleteTodo="deleteTodo" :todo="todo" />
    </div>
  
  </div>
</template>

<script setup>
import { computed, ref, onMounted } from 'vue';
import TodoItem from './TodoItem.vue';
const todos = ref([
])

const searchTerm = ref('');

const isGridLayout = ref(false);

const newTodo = ref('');
const isLoading = ref(true);

function toggle(todo) {
  todo.done = !todo.done
}

function deleteTodo(todo) {
  todos.value = todos.value.filter(t => t.id !== todo.id);
}

function addTodo () {
  todos.value.push({
    id: todos.value.length + 1,
    text: newTodo.value,
    done: false
  })
  newTodo.value = '';
}

const filteredTodos = computed(() => {
  return todos.value.filter(
    todo => todo.text.toLocaleLowerCase().includes(searchTerm.value.toLocaleLowerCase())
  ).sort((a, b) => b.id - a.id);
});

const fetchData =  async() => {
  const response = await fetch('https://jsonplaceholder.typicode.com/todos', {
    method: 'GET',
    headers: {
      'Content-Type': 'application/json'
    }
  });
  const data = await response.json();
  return data.map((todo, index) => {
    return {
      id: index + 1,
      text: todo.title,
      done: todo.completed
    }
  });
}
onMounted( async () => {
  isLoading.value = true;
  todos.value = await fetchData();
  isLoading.value = false;

} )

</script>

<style>
.todo-search {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 10px;
}
.layout {
  width: 80%;
  display: flex;
  flex-flow: column wrap;
}
.grid {
  flex-flow: row wrap;
  gap: 0 16px;
}
.container {
  width: 80%;
}
</style>