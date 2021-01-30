<template>
    <div id="app" class="mx-auto">
        <AddItem @submit="submitHandler"/>
        <TodoList :list="this.todoList"
                  @remove="removeHandler"/>
    </div>
</template>

<script>
    import AddItem from './components/AddItem.vue'
    import TodoList from "./components/TodoList";

    export default {
        name: 'App',
        components: {
            TodoList,
            AddItem,
        },
        methods: {
            submitHandler(todo) {
                todo = todo.toLowerCase();
                todo = todo.charAt(0).toUpperCase() + todo.slice(1);
                this.todoList = [...this.todoList, todo];
            },
            removeHandler(idx) {
                this.todoList = this.todoList.filter(el => {
                    return el.id !== idx
                })
            }
        },
        data: function () {
            return {
                todoList: [
                    {id: 1, label: 'To clean the apartment', important: false},
                    {id: 2, label: 'Make mistakes', important: false},
                    {id: 3, label: 'Fix mistakes', important: false},
                    {id: 4, label: 'Drink coffee', important: false}
                ]
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
