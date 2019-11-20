<template>
  <div class="todo">
    <h2>Todos</h2>
    <div v-for="todo in todos" v-bind:key="todo.id">
      <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import TodoItem from './TodoItem.vue';

export default Vue.extend({
  name: 'ToDoComp',
  props: ['todos'],
  components: {
    TodoItem
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
