<template>
  <h3>My to do list now</h3>
  <input
    v-model="newTodo"
    v-on:keyup.enter="addToDo"
    style="margin-bottom: 10px"
  />
  <button v-on:click="addToDo">Add to do</button>
  <ToDoItem
    v-for="item in todos"
    v-bind:todo="item"
    v-bind:key="item.id"
    @to-do-is-done="toDoIsDone(item, $event)"
    @remove-to-do="removeToDo(item)"
  />
</template>


<script>
import ToDoItem from "./ToDoItem";
export default {
  name: "ToDoList",
  data() {
    return {
      newTodo: "",
      todos: [
        { id: 1, text: "Learn JavaScript", done: false },
        { id: 2, text: "Learn Vue", done: true },
        { id: 3, text: "Build something awesome", done: false },
      ],
    };
  },
  methods: {
    addToDo: function () {
      this.todos.push({
        id: this.todos.length + 1,
        text: this.newTodo,
        done: false,
      });
      this.newTodo = "";
    },
    toDoIsDone: function (toDo, doneStatus) {
      this.todos[toDo.id - 1].done = doneStatus;
    },
    removeToDo(toDo) {
      this.todos.splice(toDo.id - 1, 1);
    },
  },
  components: {
    ToDoItem,
  },
};
</script>

<style>
h3 {
  color: rgb(34, 32, 161);
}
</style>