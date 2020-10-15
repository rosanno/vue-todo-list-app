<template>
  <div>
    <div class="add-todo">
      <form @submit="addTodo">
        <label><v-icon class="plus" color="rgb(141, 141, 141)">mdi-plus</v-icon></label>
        <input type="text" placeholder="Add Task" v-model="title">
      </form>
    </div>
  </div>
</template>

<script>
import {v4 as uuidv4} from 'uuid';

export default {
  name: "AddTodo",
  data() {
    return {
      title: '',
      titleLabel: [
        {labelTitle: 'Add Tasks', show: true}
      ]
    }
  },

  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        id: uuidv4(),
        title: this.title,
        completed: false,
        important: false
      }

      this.$emit('add-todo', newTodo);
      this.title = '';
    },

    hideLabel() {

    }
  }
}
</script>

<style scoped>
  .add-todo {
    position: absolute;
    bottom: 2%;
    margin: 2.4em 1.3em 0 1.3em;
    width: 90%;
  }

  label {
    left: 2%;
    top: 22%;
    font-size: 1.2em;
    position: absolute;
  }

  input[type="text"] {
    width: 100%;
    padding: 0.8em 0 0.8em 2.5em;
    background: rgb(41, 41, 41);
    outline: none;
    color: #fff;
  }

  ::placeholder {
    color: #fff;
    font-weight: lighter;
    font-family: sans-serif;
  }
</style>