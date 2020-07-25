<template>
  <div class="container">
    <div class="row">
      <AddTodo @on-addtodo="addTodo($event)" />
    </div>
    <div class="row">
      <div class="col-12 col-lg-6">
        <ul class="list-group">
          <TodoItem
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
import TodoItem from "./TodoItem";
import AddTodo from "./AddTodo";
export default {
  name: "TodoList",
  components: {
    TodoItem,
    AddTodo,
  },
  data() {
    return {
      todos: [
        { todoString: "Make Angular course", completed: false },
        { todoString: "Cook some food", completed: true },
        { todoString: "Make videos", completed: false },
        { todoString: "Learn Vue!", completed: true },
      ],
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push({
        todoString: newTodo,
        completed: false,
      });
    },
    toggleTodo(todo) {
      todo.completed = !todo.completed;
    },
    editTodo(todo, newString) {
      todo.todoString = newString;
    },
    deleteTodo(deleteTodo) {
      this.todos = this.todos.filter((todo) => todo !== deleteTodo);
    },
  },
};
</script>

<style></style>
