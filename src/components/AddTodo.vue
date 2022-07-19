<template>
  <div>
    <form @submit="addTodo">
      <input type="text" v-model='title' name="title" placeholder="Add Todo..." />
      <input type="submit" value="Add" class="btn btn-primary" />
    </form>
  </div>
</template>

<script>
// import { v4 as uuid } from 'uuid';
export default {
  name: 'AddTodo',
  data(){
    return{
        title: ''  // we will get this title from user input using v-model
    }
  },
  methods:{
    addTodo(event){
        event.preventDefault();
        const newTodo ={
            
            title: this.title,
            completed: false
        }
        // after we create the todo object now we need to send to data to parent i.e App.vue using the emit event
        if(this.title !== '')
           this.$emit('add-todo',newTodo);
        this.title = ''
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
}
input {
  flex: 10;
  padding: 15px;
}
input[type='submit'] {
  flex: 2;
}
.btn-primary{
  background-color: rgb(19, 123, 234);
}
</style>
