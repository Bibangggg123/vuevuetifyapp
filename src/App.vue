<template>
  <v-app>
    <todo-list />
  </v-app>
</template>

<script>
import TodoList from './components/TodoList.vue';

export default {
  components: {
    TodoList,
  },
};
</script>

<style>
html, body {
  margin: 0;
  height: 100%;
}
</style>
