<template>
  <h1 class="text-center pb-4">Vue.js Todo App</h1>
  <TodoList/>
</template>

<script>
import TodoList from "./components/TodoList.vue"

export default {
  name: 'TodoApp',
  components: {
    TodoList
  }
}
</script>