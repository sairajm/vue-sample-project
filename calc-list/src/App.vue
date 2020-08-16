<template>
  <div id="app">
    <Calculator/>
    <div class="emptyBox"></div>
    <ToDoList/>
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue'
import ToDoList from './components/ToDoList.vue'
export default {
  name: 'App',
  components: {
    Calculator,
    ToDoList,
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

.emptyBox {
  height: 100px;
  width: 800px;
}
</style>
