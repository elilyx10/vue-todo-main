<template>
  <div class="container">
    <AddTodo @addTodo="handleAddTodo($event)" />
    <TodoSingle
      @deleteTask="handleDeletedTask"
      v-for="t in TodoList"
      :key="t"
      :singleTask="t"
    />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import { Todo } from "@/models/Todo";
import AddTodo from "./AddTodo.vue";
import TodoSingle from "./TodoSingle.vue";

@Options({
  components: {
    AddTodo,
    TodoSingle,
  },
})
export default class TodoList extends Vue {
  TodoList: Todo[] = [new Todo("Äta"), new Todo("Gymma"), new Todo("Plugga")];

  handleAddTodo(t: Todo) {
    this.TodoList.push(t);
    localStorage.setItem("Todo", JSON.stringify(this.TodoList));
  }
  handleDeletedTask(todo: Todo) {
    this.TodoList.splice(this.TodoList.indexOf(todo), 1);
    localStorage.setItem("Todo", JSON.stringify(this.TodoList));
  }

  mounted() {
    if (localStorage.getItem("Todo") != null) {
      this.TodoList = JSON.parse(localStorage.getItem("Todo") || "[]");
    } else {
      return;
    }
  }
}
</script>

<style lang="scss">
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
