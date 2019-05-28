<template>
  <div id="app">
    <!--<img alt="Vue logo" src="./assets/logo.png">-->
    <!--<HelloWorld msg="Welcome to Your Vue.js App"/>-->
    <ToDoList msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
/*import HelloWorld from './components/HelloWorld.vue'*/
import ToDoList from './components/ToDoList'

export default {
  name: 'app',
  components: {
    //HelloWorld
    ToDoList
  }
}
</script>

<style>

</style>
