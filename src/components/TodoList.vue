<template>
    <div>
        <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true;}).length}}</p>
        <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false;}).length}}</p>
        <todo  v-for="todo in todos" v-bind:todo="todo" v-bind:key="todo.title"/>
    </div>
</template>

<script type="text/javascript">
  import Todo from './Todo';

  export default {
    name: 'TodoList',
    components: { Todo },
    props: {
      todos: Array
    }
  };
</script>

<style>
</style>
