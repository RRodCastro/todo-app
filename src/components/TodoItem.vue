<template>
    <div class="todo-item" :class="{'completed' : todo.done}">
        <span>
            {{ todo.text }}
        </span>
        <div class="controls">
        <input type="checkbox" :checked="todo.done" @change="toggle(todo)" />
        <button @click="deleteTodo(todo)" >Delete</button>
    </div>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';
defineProps({
    todo: {
        type: Object,
    },
    toggle: {
        type: Function,
    },
    deleteTodo: {
        type: Function,
    }
});

</script>

<style>
.todo-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: 10px 0;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    width: 200px;
}
.completed {
    text-decoration: line-through;
}
.controls {
    display: flex;
    gap: 0 10px;
}
</style>