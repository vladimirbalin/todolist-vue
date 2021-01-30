<template>
  <form class="add-item">
    <input type="text" v-model="todo"/>
    <button @click="submitHandler" class="btn btn-add btn-primary">Add todo</button>
  </form>
</template>

<script>
  export default {
    name: 'SearchInput',
    methods: {
      submitHandler: function (e) {
        e.preventDefault();
        this.$emit('submitHandler', this.todo);
        this.todo = '';
      }
    },
    data: function () {
      return {
        todo: ''
      };
    }
  }
</script>

<style scoped>
  .add-item {
    margin-top: 1rem;
  }
  .btn-add {
    margin-left: 1rem;
  }

</style>
