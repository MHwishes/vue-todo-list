<template>
    <div class="centered">
        <div class='content'>
            <h2 class='header'>
                {{ todo.title }}
            </h2>
            <p class='meta'>
                {{ todo.project }}
            </p>
            <div class='extra'>
             <span>
              <a-icon type="form"/>
              <a-icon type="delete"/>
            </span>
            </div>
        </div>
        <button class='bottom green' v-show="todo.done">
            Completed
        </button>
        <button class='bottom red' v-show="!todo.done">
            pending
        </button>
    </div>
</template>

<script type="text/javascript">
  import { Icon } from 'ant-design-vue';

  export default {
    props: ['todo'],
    components: { 'a-icon': Icon }
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

    .meta {
        color: darkgrey;
    }

    .bottom {
        height: 48px;
        line-height: 48px;
        width: 100%;
    }
</style>
