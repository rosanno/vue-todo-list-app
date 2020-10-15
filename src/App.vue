<template>
  <div id="app">
    <div class="todo-wrapper">
      <h4>My ToDo List</h4>
      <div class="tsk">
        <v-icon>mdi-home-outline</v-icon>
        <p>Tasks</p>
      </div>
      <div class="todo-content" v-bind:class="{'addScroll': addScroll}">
        <ViewTodo v-bind:todoList="todoList" @del-todo="deleteTodo"/>
      </div>
      <AddTodo @add-todo="addTodos"/>
    </div>
  </div>
</template>

<script>
import ViewTodo from "@/components/ViewTodo.vue";
import AddTodo from "@/components/AddTodo";
import {v4 as uuidv4} from 'uuid';

export default {
  name: 'App',

  components: {
    ViewTodo,
    AddTodo
  },

  data() {
    return {
      addScroll: false,
      todoList: [
        {
          id:  uuidv4(),
          title: 'Play Dota 2',
          completed: false,
          important: false
        },
        {
          id: uuidv4(),
          title: 'Update vue cli',
          completed: false,
          important: false
        },
        {
          id: uuidv4(),
          title: 'Create Vue App',
          completed: false,
          important: false
        }
      ]
    }
  },

  watch: {
    todoList: function() {
        console.log(this.todoList.length);
        if (this.todoList.length > 6) {
           this.addScroll = true
        }
    }
  },

  methods: {
    addTodos(newTodo) {
      this.todoList = [...this.todoList, newTodo]
    },

    deleteTodo(todoId) {
      console.log(todoId);
      setTimeout(() => {
        this.todoList = this.todoList.filter(todoList => todoList.id !== todoId);
      }, 500)
    }
  }
}
</script>

<style>
  * {
    margin: 0;
    padding: 0;
  }
  body {
    font-family: sans-serif;
  }
  #app {
    width: 45%;
    margin: 1.3em auto;
  }

  h4 {
    position: absolute;
    top: 2%;
    font-weight: lighter;
    color: rgb(120, 140, 222);
    font-size: 0.9rem;
  }

  .tsk {
    color: rgb(120, 140, 222);
    margin: 0 0.6em 0.5em 0.6em;
    font-weight: bold;
    font-size: 1.6em;
    display: flex;
  }

  p {
    padding: 0.1em 0 0 0.8em;
  }

  i.v-icon.notranslate.mdi.mdi-home-outline.theme--light {
    color: cornflowerblue;
    font-size: 2rem;
  }

  .todo-wrapper {
    background: rgb(26, 27, 28);
    padding: 5em 1.1em;
    position: relative;
    height: 76vh;
    border: 1px solid rgb(24, 131, 215);
  }

  .todo-content {
    height: 390px;
    scroll-behavior: smooth;
  }

  .addScroll {
    overflow-y: scroll;
  }

  ::-webkit-scrollbar {
    width: 5px;
  }

  ::-webkit-scrollbar-thumb {
    background: #888;
    border-radius: 4px;
  }

  ::-webkit-scrollbar-thumb:hover {
    background: #555;
  }
</style>
