<template>
  <div id="app">
    <div>
      <label for="">Todo</label>
      <input type="text" v-model="todo.todo">
      <label for="">Completed</label>
      <input type="checkbox" v-model="todo.completed">
      <button type="submit" @click.prevent="addTodo()">Submit</button>
    </div>
    <div>
      <p v-for="(todo,index) in todos" :key="index">
        {{ todo.todo }}, 
        Completed: {{ todo.completed }}
      </p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',
  
  data() {
    return {
      todo:{
        todo: '',
        completed: false
      },
      todos: [{}]
    }
  },

  async created() {
    const res = await axios.get('http://localhost:5000/todos');
    this.todos = res.data;
  },

  methods: {
    async addTodo(){
      try{
        const res = await axios.post('http://localhost:5000/todos', this.todo);
        this.todos.push(this.todo);
        console.log(res);
      }catch(e){
        console.log(e.response.data);
      }
    }
  }
}
</script>
