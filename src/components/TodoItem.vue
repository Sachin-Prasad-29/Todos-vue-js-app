<template>
  <!-- So here we are binding the class is-completed based on codition that if todo.completed is true apply the class is-completed -->
  <div class="todo-item" v-bind:class="{ 'is-complete': todo.completed }">
    <p>
      <input type="checkbox" @change="markComplete" />
      {{ todo.title }}
      <button v-on:click="$emit('del-todo',todo.id)" class="del"> X </button>
    </p>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todo'],
  data() {
    return {
      // here we are making the reference of the prop because we directly can't mutate the props
      todoReference: this.todo,
    };
  },
  methods: {
    markComplete() {
      this.todoReference.completed = !this.todoReference.completed;
    },
  },
};
</script>

<style scoped>
.todo-item {
  background: rgba(119, 240, 212, 0.637);
  padding: 4px 24px;
  border-bottom: 1px solid gray;
}
.is-complete {
  text-decoration: line-through;
}
.del {
  background: rgb(219, 14, 14);
  color: white;
  font-weight: 700;
  border: none;
  padding: 5px 12px;
  border-radius: 50px;
  cursor: pointer;
  float: right;
}
input{
  
}

</style>
