<template>
  <div id="app">
    <img src="./assets/logo.png" width="75px" height="75px">
    <h1 class="mt-3">Vue.js Todo List</h1>
    <div class="container">

      <section>
         <div class="row justify-content-center mt-4">
           <input v-model="inputField" v-on:keyup.enter="addTodo" class="mr-1" placeholder="Todo Item" />
           <button @click="addTodo" class="btn btn-primary">Add Todo</button>
        </div>
      </section>

       <section class="container">
          <div class="row">

             <!-- ============================ -->
             <!-- Was using this div for testing -->
             <!-- <div class="col-md-3 border border-danger">
                test
             </div> -->
             <!-- ============================ -->

             <div class="offset-md-3 col-md-6 mt-3">
                <ul class="list-group justify-content-center">
                   <li class="row list-group-item border mt-2 col-xs-1" v-for="todo in todoList">

                      <!-- <div class="" data-toggle=""> -->
                         <!-- <label class="btn btn-outline-secondary check-button"> -->

                         <div class="row align-items-center">
                           <input type="checkbox" v-on:change="toggle(todo)" v-bind:checked="todo.complete" class="col-sm-1 border border-danger">
                           <del v-if="todo.complete" class="col-sm-8">
                              <h5>{{ todo.name }}</h5>
                           </del>
                           <span v-else class="col-sm-8">
                              <h5>{{ todo.name }}</h5>
                           </span>
                           <span @click="deleteTodo(todo)" class="col-sm-2 delete ml-4">X</span>
                         </div>

                       <!-- </label> -->
                     <!-- </div> -->
                   </li>
                </ul>
             </div>

             <!-- ============================ -->
             <!-- Was using this div for testing -->
             <!-- <div class="col-md-3 border border-danger">
                test
             </div> -->
             <!-- ============================ -->

          </div>
       </section>

    </div>

  </div>
</template>

<script>
import Vue from 'vue';
import BootstrapVue from 'bootstrap-vue';
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

import test from './components/test';

export default {
  name: 'app',
  components: {
     test
 },
  methods: {
    addTodo: function(todo) {
      todo = this.inputField;
      this.todoList.push({name: todo, complete: false});
      this.inputField = '';
      console.log(this.todoList);
   },
   deleteTodo: function(todo) {
      // console.log(e.target.previousElementSibling.innerText);
      var index = this.todoList.indexOf(todo);
      // var index = e.target.previousElementSibling.innerText;
      // console.log(index);
      this.todoList.splice(index, 1);
      console.log(this.todoList);
   },
   toggle: function(todo) {
      todo.complete = !todo.complete;
   }
 },
  data () {
    return {
      inputField: '',
      todoList: []
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

h5 {
   margin-bottom: 0px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

/* li .delete {
   display: none;
}

li:hover .delete {
   display: inline-block;
} */

/* .checkbox {
   position: static;
   left: 0;
} */

/* li::before {
   content: "";
} */

.delete {
   color: pink;
   cursor: pointer;
   /* position: absolute; */
}

.delete:hover {
   color: red;
}
</style>
