<template>
    <div class='todoForm'>
        <button class='plus-icon button' v-show="!isCreating" v-on:click="openForm">
            <a-icon type="plus"/>
        </button>
        <div class='centered' v-show="isCreating">
            <div class='content'>
                <div class='ui form'>
                    <div class='field'>
                        <label>Title: </label>
                        <input v-model="titleText" type='text' ref='title' defaultValue="">
                    </div>
                    <div class='field'>
                        <label>Project: </label>
                        <input type='text' ref='project' defaultValue="" v-model="projectText">
                    </div>
                    <div class='buttons'>
                        <button class=' blue button' v-on:click="createForm">
                            Create
                        </button>
                        <button class='red button' v-on:click="closeForm">
                            Cancel
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
  import { Icon } from 'ant-design-vue';

  export default {
    components: { 'a-icon': Icon },
    data() {
      return {
        titleText: '',
        projectText: '',
        isCreating: false,
      };
    },
    methods: {
      openForm: function () {
        this.isCreating = true;
      },
      closeForm: function () {
        this.titleText = '';
        this.projectText = '';
        this.isCreating = false;
      },
      createForm: function () {
        this.isCreating = false;
        const title = this.titleText;
        const project = this.projectText;
        this.$emit('addTodo', {
          title,
          project,
          done: false
        });
      }
    }
  };
</script>

<style>
    .centered {
        margin-bottom: 48px;
        border: 1px solid #595959;
        border-radius: 5px;
        box-shadow: 1px 1px 1px #888888;
    }

    .red {
        border: 1px solid red;
        color: red;
    }

    .blue {
        border: 1px solid #176fff;
        color: #176fff;
    }

    .todoForm {
        width: 360px;
        margin: 0 auto;
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

    .plus-icon {
        border: 1px solid #7dff6b;
        color: #7dff6b;
    }
</style>
