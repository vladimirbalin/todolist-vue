<template>
    <div class="todo-list-item">
        <span class="todo-list-item-label">
            {{todo}}
        </span>
        <button @click="removeHandler" class="btn btn-danger p-1"><i class="bi bi-trash2-fill"></i></button>
    </div>
</template>

<script>
    export default {
        name: 'TodoItem',
        props: {
            todo: {
                type: String
            },
            id: {
                type: Number
            },
            remove: {
                type: Function
            }
        },
        methods: {
            removeHandler: function () {
                this.$emit('remove', this.id)
            }
        },
    }
</script>

<style>
    .todo-list-item {
        text-align: left;
        font-size: 1.25rem;
    }

    .todo-list-item button {
        width: 35px;
        margin: 3px;
    }

    .todo-list-item-label {
        margin-left: 1.25rem;
        line-height: 35px;
        user-select: none;
    }

</style>
