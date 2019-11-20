<template>
  <div class="add-todo">
    <form @submit.prevent="addTodo">
      <input type="text" name="title" placeholder="Add Todo..." v-model="title" />
      <input type="submit" value="submit" class="btn" />
    </form>
  </div>
</template>

<script>
import Chance from 'chance';

export default {
  name: 'AddTodo',
  data() {
    return {
      title: ''
    };
  },
  methods: {
    addTodo() {
      const newTodo = {
        id: new Chance().guid(),
        title: this.title,
        completed: false
      };
      this.title = '';

      this.$emit('added-todo', newTodo);
    }
  }
};
</script>

<style scoped lang="scss">
form {
  display: flex;
}
input {
  &[type='text'] {
    flex: 10;
    padding: 5px;
  }
  &[type='submit'] {
    flex: 2;
  }
}
</style>
