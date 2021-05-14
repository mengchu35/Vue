<template>
  <div id="app">
    <todoList msg="todoList"/>
  </div>
</template>

<script>
import todoList from './components/practice3.vue'
import '../node_modules/@fortawesome/fontawesome-free/css/all.css'

export default {
  name: 'App',
  components: {
    todoList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
