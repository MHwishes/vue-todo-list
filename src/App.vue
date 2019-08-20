<script>
  // import HelloWorld from './components/HelloWorld.vue';
  import TodoList from './components/TodoList';

  export default {
    name: 'app',
    components: {
      TodoList
    },
    data() {
      return {
        todos: [{
          title: 'Todo A',
          project: 'Project A',
          done: false,
        }, {
          title: 'Todo B',
          project: 'Project B',
          done: true,
        }, {
          title: 'Todo C',
          project: 'Project C',
          done: false,
        }, {
          title: 'Todo D',
          project: 'Project D',
          done: false,
        }]
      };
    }
  };
</script>

<template>
    <div id="app">
        <h1>Todos</h1>
        <todo-list v-bind:todos="todos"></todo-list>
    </div>
</template>
<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
    h1{
        color: #cb1931;
    }
</style>
