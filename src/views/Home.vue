<template>
  <div class="home">
    <h1>{{ msg }}</h1>
    <AddTodo v-on:added-todo="addThisTodo" />
    <ToDoComp v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';
import ToDoComp from '@/components/ToDoComp';
import AddTodo from '@/components/AddTodo';
import handleErrors from '@/utils/handleErrors';

export default {
  name: 'home',
  props: {
    msg: String
  },
  components: {
    ToDoComp,
    AddTodo
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    deleteTodo(idToDelete) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${idToDelete}`)
        .then(res => {
          this.todos = this.todos.filter(tod => tod.id !== idToDelete);
        })
        .catch(err => handleErrors.toss(err));
    },
    addThisTodo(newTodo) {
      const { title, completed } = newTodo;

      axios
        .post('https://jsonplaceholder.typicode.com/todos', {
          title,
          completed
        })
        .then(res => this.todos.unshift(res.data))
        .catch(err => handleErrors.toss(err));
    }
  },
  created() {
    axios
      .get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => {
        this.todos = res.data;
      })
      .catch(err => handleErrors.toss(err));
  }
};
</script>
