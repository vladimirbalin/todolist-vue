<template>
    <div class="todo-list-item">
          <span class="todo-list-item-label">
        {{msg}}
      </span>
    </div>
</template>

<script>
    export default {
        name: 'TodoItem',
        props: {
            msg: {
                type: String
            }
        }
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
