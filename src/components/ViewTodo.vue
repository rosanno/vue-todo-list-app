<template>
  <div>
    <div v-for="todo in todoList" v-bind:key="todo.id">
      <TodoItems v-bind:todo="todo" @delete-todo="$emit('del-todo', todo.id)"/>
    </div>
  </div>
</template>

<script>
import TodoItems from "@/components/TodoItems";

export default {
  name: 'ViewTodo',
  components: {
    TodoItems,
  },
  props: {
    todoList: {
      type: Array,
      required: false
    }
  },

  data() {
    return {

    }
  }

}
</script>

<style scoped>

</style>