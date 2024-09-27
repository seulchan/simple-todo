<template>
    <li class="todo-item">
        <span class="todo-text">{{ todo.text }}</span>
        <button @click="deleteTodo" class="delete-btn">Delete</button>
    </li>
</template>

<script>
export default {
    props: {
        todo: Object
    },
    methods: {
        deleteTodo() {
            this.$emit('delete-todo', this.todo.id);
        }
    }
};
</script>

<style>
.todo-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
    margin-bottom: 10px;
    background-color: white;
}

.todo-text {
    flex-grow: 1;
    font-size: 1.1em;
    font-family: 'Arial', sans-serif;
}

.delete-btn {
    background-color: #d9534f;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    padding: 5px 10px;
}

.delete-btn:hover {
    background-color: #c9302c;
}
</style>