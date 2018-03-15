<template>
  <div class='ui centered card'>
    <!-- // Todo shown when we are not in editing mode. -->
    <div class="content" v-show="!isEditing">
      <div class='header'>
          {{ todo.title }}
      </div>
      <div class='description'>
          {{ todo.project }}
      </div>
      <div class='extra'>
          <span class='right floated edit icon' v-on:click="showForm">
            <i class='edit icon'></i>
          </span>
         <span class='right floated trash icon' v-on:click="deleteTodo(todo)">
          <i class='trash icon'></i>
        </span>
      </div>
    </div>
    <!-- // form is visible when we are in editing mode -->
    <div class="content" v-show="isEditing">
      <div class='ui form'>
        <div class='field'>
          <label>Title</label>
          <input type='text' v-model="todo.title" >
        </div>
        <div class='field'>
          <label>Project</label>
          <input type='text' v-model="todo.project" >
        </div>
        <div class='ui button attached buttons'>
          <button class='ui blue button' v-on:click="hideForm">
            Close
          </button>
        </div>
      </div>
    </div>
    <div class='ui bottom attached positive button' v-on:click="pendingTodo(todo)" v-show="!isEditing &&todo.done" disabled>
        Completed
    </div>
    <div class='ui bottom attached negative button' v-on:click="completeTodo(todo)" v-show="!isEditing && !todo.done">
        Pending
    </div>
  </div>
</template>

<script type="text/javascript">
export default {
  props: ['todo'],
  data() {
    return {
      isEditing: false,
    };
  },
  methods: {
    completeTodo(todo) {
      this.$emit('complete-todo', todo);
    },
    pendingTodo(todo) {
      this.$emit('pending-todo', todo);
    },
    deleteTodo(todo) {
      this.$emit('delete-todo', todo);
    },
    showForm() {
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    },
  },
};
</script>

