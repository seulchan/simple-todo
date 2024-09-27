<template>
    <div class="todo-list-container">
        <h2 class="todo-list-title">Your To-do List</h2>
        <ul class="todo-list">
            <todo-item v-for="todo in todos" :key="todo.id" :todo="todo" @delete-todo="deleteTodo" />
        </ul>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
    props: {
        todos: Array
    },
    components: {
        TodoItem
    },
    methods: {
        deleteTodo(todoId) {
            this.$emit('delete-todo', todoId);
        }
    }
};
</script>

<style>
.todo-list-container {
    margin-top: 20px;
}

.todo-list {
    list-style-type: none;
    padding: 0;
}
</style>