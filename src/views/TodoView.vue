<template>
  <div class="showHello">
    <TodoList msg="Todo List" :todos="todos"/>

  <form @submit.prevent="onSubmit()">
  <td>
    <input v-model="name" type= "text" class= "inputTodos" placeholder="Input your Todo List here..." /> 
  </td>
  <td>
    <button class="button" type="submit">Tambahkan</button>
  </td>
  <p>{{ showHebat }}</p>
</form>
  </div>
</template>

<script>
import TodoList from '@/components/TodoList.vue'

export default {
  name: "TodoView",
  components: {
    TodoList,
  },
  data (){
    return {
      name : '',
      showError: false,
      todos: [],
    };
  },
  computed: {
    showHebat: function () {
      if (this.todos.length >= 4) {
        return "Hebat!";
      }
      return "";
    },
  },
  methods : {
    onSubmit: function () {
    if (!this.name) {
        this.showError = true;
        return false,
        alert("Input your Todo!");
      }
      this.todos.push(this.name);
      this.name = "";
      this.showError = false;
    },
  },
}
</script>
<style>
.h1 {
    padding-top: 20px;
    font-size: large;
    font-weight: bold;
}
.name {
    width: 85%;
    display: flex;
    justify-content: space-between;
    padding: 12px;
    border: 1px solid #ccc;
    border-radius: 4px;
    resize: vertical;
    font-size: 40px;
}
.button{
    display: flex;
    justify-content: flex-end;
    padding: 12px;
    border: 1px solid #ccc;
    border-radius: 4px;
    resize: vertical;
}
</style>
