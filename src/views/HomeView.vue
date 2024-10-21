<template>
  <div class="px-3 py-10 md:px-10">
    <div class="w-full sm:w-1/2 lg:w-1/3 mx-auto">
      <TodoSpinner />

      <TodoFormAdd />

      <TodoItems />

      <TodoEmpty />
    </div>
  </div>
</template>

<script>
import TodoEmpty from "@/components/TodoEmpty.vue";
import TodoFormAdd from "@/components/TodoFormAdd.vue";
import TodoItems from "@/components/TodoItems.vue";
import TodoSpinner from "@/components/TodoSpinner.vue";
import axios from "axios";

// @ is an alias to /src

export default {
  name: "HomeView",
  components: { TodoSpinner, TodoFormAdd, TodoItems, TodoEmpty },

  data() {
    return {
      todos: [],
    };
  },

  async created() {
    this.todos = await axios
      .get("http://localhost:3000/todos")
      .then((response) => response.data)
      .catch((error) => console.log(error));
  },
};
</script>
