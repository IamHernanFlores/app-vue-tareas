<template>
  <div>
    <div id="header">
      <Search v-on:query-change="querySearch" />
    </div>

    <div id="main-container">
      <h2>Lista de tareas 🏁</h2>
      <TodoAdd v-on:add-todo="addTodo"/>
      <Todos v-bind:todoslist="copyTodos" v-on:delete-todo="deleteTodo" />
    </div>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import Search from './components/Search';
import Todos from './components/Todos';
import TodoAdd from './components/TodoAdd';

export default {
  name: 'App',
  components: {
    Todos, TodoAdd, Search
  },
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id != id);
      this.copyTodos = [...this.todos];
    },
    addTodo(todo){
      this.todos.push(todo);
      this.copyTodos = [...this.todos];
    },
    querySearch(query){
      if(query.trim() === ''){
        this.copyTodos = [...this.todos];
      }else{
        const temp = this.todos.filter(todo =>{
          return todo.title.includes(query)
        });

        this.copyTodos = [...temp];
      }
    }
  }, // Cargando datos 
  data(){
    return {
      todos: [
        {
          id: 0,
          title:  'Hacer las compras 🍔',
          completed: false
        },
        {
         id: 1,
         title: 'Estudiar 2hs 📕',
         completed: true
       },
       {
         id: 2,
         title: 'Jugar al futbol ⚽',
         completed: false
       },
      ], // Al ejecutar el programa devuelve lo mismo 
      copyTodos: []
    }
  }, // Funcion que replica todos los componentes 
  created(){
    this.copyTodos = [...this.todos];
  }
}
</script>

<style>
  *{
    box-sizing: border-box;
  }

  body{
    font-family: Arial, Helvetica, sans-serif;
    font-size: 1.5em;
    padding: 0;
    margin: 0;
  }

  #main-container{
    border: solid 2px rgb(129, 129, 129);
    width: 600px;
    margin: 100px auto;
    border-radius: 20px;
  }

  #header{
background: rgb(9,121,22);
background: radial-gradient(circle, rgba(9,121,22,1) 0%, rgba(56,146,67,1) 92%, rgba(245,245,245,1) 100%);  }

  h2{
    padding: 0 10px;
  }

</style>
