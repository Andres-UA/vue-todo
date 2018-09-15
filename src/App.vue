<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <br>
    <TodoList />
    
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";

export default {
  name: "app",
  components: {
    TodoList
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 400px;
  margin: 0% auto;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
