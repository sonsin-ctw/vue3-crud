<template>
  <div id="app">
    <TodoList />
  </div>
</template>

<script>
import TodoList from './components/ItemList.vue';

export default {
  components: {
    TodoList,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 10px;
}
</style>
