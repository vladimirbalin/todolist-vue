<template>
    <div id="app" class="mx-auto">
        <AddItem @submitHandler="submitHandler"/>
        <ul v-for="(msg, index) in this.todoList" :key="index">
            <TodoItem :msg="msg"/>
        </ul>
    </div>
</template>

<script>
    import AddItem from './components/AddItem.vue'
    import TodoItem from "./components/TodoItem.vue";

    export default {
        name: 'App',
        components: {
            AddItem,
            TodoItem
        },
        methods: {
            submitHandler(todo) {
                todo = todo.toLowerCase();
                todo = todo.charAt(0).toUpperCase() + todo.slice(1);
                this.todoList = [...this.todoList, todo];
            }
        },
        data: function () {
            return {
                todoList: ['To clean the apartment', 'Make mistakes', 'Fix mistakes', 'Drink coffee']
            };
        }
    }
</script>

<style>
    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }

    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
        max-width: 400px;
    }
</style>
