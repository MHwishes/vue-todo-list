<template>
    <div class="centered">
        <div class='content' v-show="!isEditing">
            <h2 class='header'>
                {{ todo.title }}
            </h2>
            <p class='meta'>
                {{ todo.project }}
            </p>
            <div class='extra'>
             <span>
              <a-icon type="form" v-on:click="showForm"/>
              <a-icon type="delete" v-on:click="deleteTodo(todo)"/>
            </span>
            </div>
        </div>
        <div class="content" v-show="isEditing">
            <div class='form'>
                <div class='field'>
                    <label>Title:</label>
                    <input type='text' placeholder="" v-model="titleText"/>
                </div>
                <div class='field'>
                    <label>Project: </label>
                    <input type='text' placeholder="" v-model="projectText"/>
                </div>
                <div class='buttons'>
                    <button class='blue button' v-on:click="editForm(todo)">
                        edit
                    </button>
                    <button class='red button' v-on:click="hideForm">
                        Cancel
                    </button>
                </div>
            </div>
        </div>
        <button class='bottom green' v-show="!isEditing&&todo.done">
            Completed
        </button>
        <button class='bottom red' v-show="!isEditing&&!todo.done">
            pending
        </button>
    </div>
</template>

<script type="text/javascript">
  import { Icon } from 'ant-design-vue';

  export default {
    props: ['todo'],
    components: { 'a-icon': Icon },
    data() {
      return {
        isEditing: false,
        titleText: this.todo.title,
        projectText: this.todo.project
      };
    },
    methods: {
      showForm: function () {
        this.isEditing = true;
      },
      hideForm() {
        this.isEditing = false;
      },
      editForm(todo) {
        this.isEditing = false;
        this.$emit('edit-todo', { title: this.titleText, project: this.projectText, done: false }, todo);
      },
      deleteTodo: function (todo) {
        this.$emit('delete-todo', todo);
      }
    }
  };
</script>

<style scoped>
    .centered {
        margin-bottom: 48px;
        border: 1px solid #595959;
        border-radius: 5px;
        box-shadow: 1px 1px 1px #888888;
    }

    .green {
        border: 1px solid green;
        color: green;
    }

    .red {
        border: 1px solid red;
        color: red;
    }

    .blue {
        border: 1px solid #176fff;
        color: #176fff;
    }

    .meta {
        color: darkgrey;
    }

    .bottom {
        height: 48px;
        line-height: 48px;
        width: 100%;
    }

    .field {
        margin: 16px 0;
    }

    label {
        font-size: 18px;
        font-weight: 700;
    }

    input {
        outline: none;
        border: 1px solid #595959;
        border-radius: 4px;
        width: 60%;
    }

    .button {
        width: 30%;
        border-radius: 12px;
    }

    .buttons {
        display: flex;
        justify-content: space-around;
        margin-bottom: 24px;
    }


</style>
