<template>
  <div id="app">
    <addTodo v-on:add="pushTodo"/>
    <Todos v-bind:todos="todos" v-on:del="deleteTodo" v-on:update="updateTodo"/>
    <hr class="col-md-6 offset-md-3"/>
    <div class="col-md-6 mt-3 offset-md-3 d-flex justify-content-between">
      <div>Check all <input type="checkbox" :checked="checked" @change="checkAll"/></div>
      <div>Todos left: {{remaining}}</div>
    </div>
  </div>
</template>

<script>
import Todos from './components/Todos.vue'
import addTodo from './components/addTodo.vue'

export default {
  name: 'app',
  components:{
    Todos,
    addTodo,
  },
  computed:{
    remaining(){
      return this.todos.filter((todo) => todo.status !== true).length;
    },
    checked(){
      return this.remaining == 0;
    }
  },
  data(){
    return{
      todos:[
        {
          id:1,
          title:'Precious is a trouble maker',
          status:true,
        },
        {
          id:2,
          title:'It is about to go down',
          status:false,
        },
        {
          id:3,
          title:'Vue is sweet',
          status:false,
        },
        {
          id:4,
          title:'Praise jah with me',
          status:false,
        },
        {
          id:5,
          title:'Play football with Dami',
          status:true,
        },
         {
          id:6,
          title:'Eze goes to school',
          status:true,
        },
        {
          id:7,
          title:'Simbi is a village girl',
          status:false,
        },
        {
          id:8,
          title:'Ja Ja Okocha is a player',
          status:false,
        },
        {
          id:9,
          title:'Nkolika geos to school',
          status:false,
        },
        {
          id:10,
          title:'Give vue a chance',
          status:true,
        },
      ]
    }
  },
  methods:{
    pushTodo(newTodo){
      this.todos.push(newTodo);
    },
    deleteTodo(todo){
       this.todos.splice(this.todos.indexOf(todo), 1);
    },
    checkAll(){
      // console.log('CheckAll');
      this.todos.forEach((todo) => todo.status = event.target.checked)
    },
    updateTodo(value){
      console.log(value);
      //  this.todos.splice(this.todos.indexOf(UpdatedTodo), 1, UpdatedTodo);
      
    }
  }
}
</script>

<style scoped>

</style>
