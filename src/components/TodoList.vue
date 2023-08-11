<template>
    <div class="showHello">
      <h1>{{ msg }}</h1>
   
    
    <ol v-show="showTodos">
    <td>
      <li v-for="(todo, index) in todos" v-bind:key="index">
        {{ todo }}
    </li>
    </td>
    <td>
        <button>Delete</button>
    </td>
    <td>
        <button>Edit</button>
    </td>
    </ol>
    </div>
   
</template>
<script>
export default {
    name: 'TodoList',
    computed: {
    showTodos: function () {
      return this.todos.length > 0;
    },
  },
    props: {
        msg: String,
        todos: Array
    },
};
</script>

<style scoped>

</style>