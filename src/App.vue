<template>
<div id="app">
  <!-- https://scotch.io/tutorials/build-a-to-do-app-with-vue-js-2 -->
  <h1 class="ui dividing centered header">Vue.js Todo App</h1>
  <div class='ui three column centered grid'>
    <div class='column'>
      <to-do-list v-bind:todos="todos"></to-do-list>
      <create-todo v-on:create-todo="createTodo"></create-todo>
    </div>
  </div>
</div>
</template>

<script>
import ToDoList from './components/ToDoList';
import CreateTodo from './components/CreateTodo';

export default {
  name: 'app',
  components: {
    ToDoList,
    CreateTodo,
  },
  data() {
    return {
      todos: [{
        title: 'Create a To Do List',
        project: 'Create a To Do List with Vue.js',
        done: true,
      }, {
        title: 'Publish to Website',
        project: 'Showcase Vue app to website',
        done: false,
      }, {
        title: '???',
        project: '',
        done: false,
      }, {
        title: 'Profit!',
        project: '',
        done: true,
      }],
    };
  },
  methods: {
    createTodo(newTodo) {
      this.todos.push(newTodo);
    },
  },
};
</script>

<style src="./assets/styles.css"></style>