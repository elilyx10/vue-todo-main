<template>
  <form class="createContainer">
    <input type="text" placeholder="Write something you want to do..." v-model="description" />
    <button class="btn btn--add" @click="addTodo">Add</button>
  </form>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";
import { Todo } from "@/models/Todo";
import { Prop } from "vue-property-decorator";

export default class AddTodo extends Vue {
  @Prop() saveBtn!: string;
  description = "";

  addTodo() {
    this.$emit("addTodo", new Todo(this.description));
    this.description = "";
  }
}
</script>

<style lang="scss" scoped>
input {
  border: solid 1px;
  border-radius: 5px;
  background-color: white;
  height: 50px;
  width: 250px;
  text-align: center;
}
.btn--add {
  border: solid 1px;
  border-radius: 5px;
  border-color: blue;
  background-color: white;
  color:black;
  width: 50px;
  height: 50px;
}

.btn {
  height: 50px;
  width: 100px;
}

.createContainer {
  display: flex;
  gap: 15px;
  margin-bottom: 25px;
}

@media only screen and (max-width: 768px) {
  .createContainer {
    width: 80%;
  }
}
</style>
