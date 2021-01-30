<template>
    <ul>
        <TodoItem v-for="(item, index) in this.list"
                  :key="index"
                  :todo="item.label"
                  :id="item.id"
                  v-on="$listeners"
        />
    </ul>
</template>

<script>
    import TodoItem from "./TodoItem";

    export default {
        name: "TodoList",
        components: {
            TodoItem
        },
        props: {
            list: {
                type: Array
            },
        },
    }

</script>

<style scoped>

</style>