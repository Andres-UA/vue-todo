<template>  
    <div class="siimple-content siimple-content--small">
        <center>
        <img alt="Vue logo" src="./assets/logo.png">
        </center>
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
    @import url('https://cdn.jsdelivr.net/npm/siimple@3.1.1/dist/siimple.min.css');
    @import url('https://use.fontawesome.com/releases/v5.3.1/css/all.css');
    #app {
        font-family: "Avenir", Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        
        color: #2c3e50;
        margin-top: 60px;
    }

</style>
