<template>
    <div id="app" class="mx-auto">
        <AddItem @submit="submitHandler"/>
        <TodoList :list="this.todoList"
                  @remove="removeHandler"
                  @important="importantHandler"/>
    </div>
</template>

<script>
    import AddItem from './components/AddItem.vue'
    import TodoList from "./components/TodoList";
    import { v4 as uuidv4 } from 'uuid';

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
                this.todoList = [...this.todoList, {id: uuidv4(), label: todo, important: false }];
            },
            removeHandler(idx) {
                this.todoList = this.todoList.filter(el => {
                    return el.id !== idx
                })
            },
            importantHandler(idx) {
                const indexOfChangedItem = this.todoList.findIndex(el => el.id === idx);
                const changedItem = {
                    ...this.todoList[indexOfChangedItem],
                    important: !this.todoList[indexOfChangedItem].important
                }
                console.log(indexOfChangedItem, ' ', changedItem)
                this.todoList = [
                    ...this.todoList.slice(0, indexOfChangedItem),
                    changedItem,
                    ...this.todoList.slice(indexOfChangedItem + 1)
                ]
            }
        },
        data: function () {
            return {
                todoList: [
                    {id: uuidv4(), label: 'To clean the apartment', important: false},
                    {id: uuidv4(), label: 'Make mistakes', important: false},
                    {id: uuidv4(), label: 'Fix mistakes', important: true},
                    {id: uuidv4(), label: 'Drink coffee', important: true}
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
