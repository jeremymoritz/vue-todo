<template>
  <div class="home">
    <Header />
    <h1>{{ msg }}</h1>
    <AddTodo v-on:added-todo="addThisTodo" />
    <ToDoComp v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
// @ is an alias to /src
import ToDoComp from '@/components/ToDoComp.vue';
import Header from '@/components/layout/Header';
import AddTodo from '@/components/AddTodo';

export default {
  name: 'home',
  props: {
    msg: String
  },
  components: {
    ToDoComp,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: [
        { id: 1, title: 'Todo One', completed: false },
        { id: 2, title: 'Todo Two', completed: true },
        { id: 3, title: 'Todo Three', completed: false }
      ]
    };
  },
  methods: {
    deleteTodo(idToDelete) {
      this.todos = this.todos.filter(tod => tod.id !== idToDelete);
    },
    addThisTodo(newTodo) {
      this.todos.push(newTodo);
    }
  }
};
</script>
