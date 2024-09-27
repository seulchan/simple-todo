<template>
    <div class="add-todo-container">
        <input type="text" v-model="newTodoText" @keyup.enter="addTodo" placeholder="Enter new to-do"
            class="todo-input" />
        <button @click="addTodo" class="add-btn">Add To-do</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            newTodoText: ''
        };
    },
    methods: {
        addTodo() {
            if (this.newTodoText.trim() === '') return;

            const newTodo = {
                id: Date.now(),
                text: this.newTodoText
            };

            this.$emit('add-todo', newTodo);

            this.newTodoText = '';
        }
    }
};
</script>

<style>
.add-todo-container {
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;
}

.todo-input {
    flex-grow: 1;
    padding: 10px;
    border: 2px solid #ccc;
    border-radius: 5px;
    font-size: 1.1em;
    margin-right: 10px;
}

.add-btn {
    background-color: #5cb85c;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 1.1em;
}

.add-btn:hover {
    background-color: #4cae4c;
}
</style>