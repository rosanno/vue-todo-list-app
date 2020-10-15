<template>
   <div>
     <div class="todo-list">
       <div class="items">
         <v-btn icon>
           <v-icon title="Mark as complete" v-if="!this.todo.completed" @click="markComplete">mdi-checkbox-blank-circle-outline</v-icon>
           <v-icon title="Mark as complete" v-else @click="markedIncomplete">mdi-checkbox-marked-circle</v-icon>
         </v-btn>
         <p class="todo-title" v-bind:class="{'completed': todo.completed }">{{ todo.title }}</p>
         <v-spacer></v-spacer>
           <div class="float-right">
             <v-btn icon>
               <v-icon  height="24" width="24" v-if="!this.todo.important" @click="markedImportant">mdi-star-outline</v-icon>
               <v-icon  height="24" width="24" v-else @click="markedNotImportant">mdi-star</v-icon>
             </v-btn>
           </div>
           <div class="trash">
             <v-btn icon>
               <v-icon icon height="24" width="24" @click="deleteTodo">mdi-trash-can-outline</v-icon>
             </v-btn>
           </div>
       </div>
     </div>
   </div>
</template>

<script>

export default {
  name: 'Todoitems',
  props: {
     todo: {
       type: Object
     }
  },

  data() {
     return {

     }
  },

  components: {

  },

  methods: {
     markComplete() {
       let check = this.todo.completed = !this.todo.completed;
       console.log(check)
     },

    markedIncomplete() {
       this.todo.completed = !this.todo.completed;
    },

    markedImportant() {
       this.todo.important = !this.todo.important;
    },

    markedNotImportant() {
       this.todo.important = !this.todo.important;
    },

    deleteTodo() {
      this.$emit('delete-todo', this.todo.id);
    },
  },

  computed: {

  }
}
</script>
<style scoped>
  .items {
    color: rgb(106, 106, 106);
    background: rgb(43, 43, 45);
    padding: 0.9em 0 0.9em 0.7em;
    margin: 0.3em 1.4em 0 1.4em;
    border-radius: 4px;
    font-size: 0.9em;
    position: relative;
    display: flex;
  }

  .items:hover {
    background: rgb(41, 41, 41);
  }

  .trash {
    position: absolute;
    right: 1%;
    top: 20%;
  }

  .float-right {
    position: absolute;
    right: 5%;
    top: 20%;
  }

  input[type="checkbox"] {
    margin: 0.5em 1.1em 0 0;
    border: none;
    background: none;
  }

  .completed {
    text-decoration: line-through;
    color: rgb(141, 141, 141);
  }

  .todo-title {
    margin: 0.6em 0.8em;
  }

  .v-btn--outlined .v-btn__content .v-icon[data-v-4baca61a], .v-btn--round .v-btn__content .v-icon[data-v-4baca61a] {
    color: cornflowerblue;
  }

  button.v-icon.notranslate.v-icon--link.mdi.mdi-checkbox-blank-circle-outline.theme--light {
    color: rgb(141, 141, 141);
  }

  button.v-icon.notranslate.v-icon--link.mdi.mdi-star-outline.theme--light {
    color: rgb(141, 141, 141);
  }

  button.v-icon.notranslate.v-icon--link.mdi.mdi-trash-can-outline.theme--light {
    color: rgb(141, 141, 141);
  }

  .remove {
    transform: translateX(-20%);
    transition: ease-in 300ms;
  }
</style>