<template>
  <div class="showHello">
    <h1>{{ msg }}</h1>
 
    <table v-show="showTodos">
      <tbody>
        <ol>
          <li v-for="(todo, index) in todos" :key="index">
            <tr>
              <td v-if="editingIndex !== index">
                {{ todo }}
              </td>
              <td v-else>
                <input type="text" v-model="editedTodo" @keyup.enter="saveEdit(index)" />
              </td>
              <td>
                <button @click="deleteTodo(index)">Delete</button>
              </td>
              <td>
                <button @click="toggleEdit(index)">
                  {{ editingIndex === index ? 'Save' : 'Edit' }}
                </button>
              </td>
            </tr>
          </li>
        </ol>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  data() {
    return {
      editingIndex: -1,
      editedTodo: '',
    };
  },
  computed: {
    showTodos: function () {
      return this.todos.length > 0;
    },
  },
  props: {
    msg: String,
    todos: Array,
  },
  methods: {
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
    toggleEdit(index) {
      if (this.editingIndex === index) {
        this.saveEdit(index);
      } else {
        this.startEdit(index);
      }
    },
    startEdit(index) {
      this.editingIndex = index;
      this.editedTodo = this.todos[index];
    },
    cancelEdit() {
      this.editingIndex = -1;
      this.editedTodo = '';
    },
    saveEdit(index) {
      this.todos[index] = this.editedTodo;
      this.editingIndex = -1;
      this.editedTodo = '';
    },
  },
};
</script>

<style scoped>
button{
    display: flex;
    justify-content: flex-end;
    padding: 12px;
    border: 1px solid #ccc;
    border-radius: 4px;
    resize: vertical;
}
</style>
