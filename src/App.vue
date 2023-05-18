<template>
  <div>
    <h1 class="titleText">VueToDo</h1>
    <TodoList />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import TodoList from "./components/TodoList.vue";

@Options({
  components: {
    TodoList,
  },
})

export default class App extends Vue {}

</script>

<style lang="scss">
body {
  font-family: 'Times New Roman', Times, serif;
  padding: 0px;
  margin: 0px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: start;
  color: black;
}

.titleText {
  display: flex;
  font-size: 46px;
  justify-content: center;
}
</style>
