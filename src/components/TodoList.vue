<template>
    <div>
        <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true;}).length}}</p>
        <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false;}).length}}</p>
        <div class="todo-list">
            <todo v-for="todo in todos" v-bind:todo="todo" v-bind:key="todo.title"
                  v-on:delete-todo="deleteTodo" v-on:edit-todo="editTodo"/>
        </div>
    </div>
</template>

<script type="text/javascript">
  import Todo from './Todo';

  export default {
    name: 'TodoList',
    components: { Todo },
    props: {
      todos: Array
    },
    methods: {
      deleteTodo: function (todo) {
        const index = this.todos.indexOf(todo);
        this.todos.splice(index, 1);
      },
      editTodo: function (newTodo, todo) {
        const index = this.todos.indexOf(todo);
        this.todos.splice(index, 1,newTodo);
      }
    }
  };
</script>

<style scoped>
    .todo-list {
        width: 360px;
        margin: 0 auto;
    }
</style>
