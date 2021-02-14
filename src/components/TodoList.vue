<template>
  <div class="container">
    <div class="row">
      <div class="col-12"><p class="display-3">Vue Crash Course</p></div>
    </div>
    <div class="row">
      <p>Add create form</p>
    </div>
    <div class="row">
      <div class="col-12 col-lg-6">
        <ul class="list-group">
          <Todo
            v-for="(todo, index) in todos"
            :key="index"
            :todoString="todo.todoString"
            :completed="todo.completed"
            @on-delete="deleteTodo(todo)"
            @on-toggle="toggleTodo(todo)"
            @on-edit="editTodo(todo, $event)"
          />
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from "./Todo";
export default {
  components: {
    Todo,
  },
  data() {
    return {
      todos: [
        { todoString: "Make Angular Course", completed: false },
        { todoString: "Make React Course", completed: false },
        { todoString: "Make Flutter Course", completed: true },
        { todoString: "Make ML Course", completed: true },
      ],
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push({ todoString: newTodo, completed: false });
    },
    toggleTodo(todo) {
      todo.completed = !todo.completed;
    },
    editTodo(todo, newTodoString) {
      todo.todoString = newTodoString;
    },
    deleteTodo(deleteTodo) {
      this.todos = this.todos.filter(
        (todo) => todo.todoString !== deleteTodo.todoString
      );
    },
  },
};
</script>

<style>
</style>