<template>
  <ul class="col-lg-6 col-sm-8 col-11 list-group align-items-center">
    <TodoItem
      v-for="todo in todos"
      :id="todo.id"
      :key="todo.id"
      :text="todo.text"
    />
    <button @click="addTodo" class="btn btn-primary mt-3 vw-25">
      Add new entry
    </button>
  </ul>
</template>

<script>
import ls from "local-storage";
import { v4 as createUuid } from "uuid";
import TodoItem from "./TodoItem.vue";

export default {
  data() {
    return {
      todos: ls.get("todoData") ? ls.get("todoData") : [],
    };
  },
  components: {
    TodoItem,
  },
  methods: {
    async addTodo() {
      const id = createUuid();
      this.todos.push({
        id: id,
      });
      ls.set("todoData", this.todos);
      await this.$nextTick();
      document.getElementById(id).focus();
    },
    removeTodo(index) {
      this.todos = this.todos.filter((entry) => entry.id !== index);
      ls.set("todoData", this.todos);
    },
    updateTodo(index, content) {
      this.todos.find((todo) => todo.id === index).text = content;
      ls.set("todoData", this.todos);
    },
  },
};
</script>
