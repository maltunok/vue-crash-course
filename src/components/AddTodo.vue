/* eslint-disable vue/comment-directive */
<template>
  <div>
    <form @submit="addTodo"></form>
    <input type="text" v-model="title" name="title" placeholder="Add Todo...">
    <input type="submit" value="Submit" class="btn">  
  </div>
</template>

<script>
//import uuid from 'uuid'
export default {
  name: 'AddTodo',
  data(){
    return{
      title: ''
    }
  },
  methods:{
    addTodo(e){
      e.preventDefault();
      const newTodo = {
        //id: uuid.v4(),
        title: this.title,
        completed: false
      }
      // send up to parent
      this.$emit('add-todo', newTodo);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
form{
  display: flex;
}
input[type="text"]{
  flex:10;
  padding: 5px;
}
input[type="submit"]{
  flex:2;
}
</style>
