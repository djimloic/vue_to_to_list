<template>
  <div class="toDoItem" v-bind:class="{ done: todoData.done }">
    <input
      type="checkbox"
      v-model="todoData.done"
      @click="$emit('toDoIsDone', !todoData.done)"
    />
    {{ todoData.text }}
  </div>
</template>

<script>
export default {
  name: "ToDoItem",
  props: {
    todo: { text: String, done: Boolean },
  },
  data: function () {
    return {
      todoData: { ...this.todo },
    };
  },
};
</script>

<style>
.toDoItem {
  color: rgb(44, 44, 43);
  font-size: 16px;
  font-weight: bold;
}

.toDoItem.done {
  text-decoration: line-through;
  color: rgb(111, 161, 32);
}
</style>