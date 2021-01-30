<template>
    <ul>
        <TodoItem v-for="(item, index) in this.list"
                  :key="index"
                  :todo="item"
                  v-on="$listeners"
                  v-bind:class="{ 'important': item.important }"
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
    .important {
        font-weight: bold;
        color: #bb4242;
    }
</style>