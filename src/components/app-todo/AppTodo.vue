<template>
  <section class="todo">

    <header>
      <h1>Todo</h1>
      <input type="text" class="new-todo" placeholder="Add a task" v-model="newTodo" @keyup.enter="addTodo"> 
    </header>

    <section class="main">
      <input class="all-check" type="checkbox" v-model="allDone" v-show="hasTodos">

      <ul class="todo-list">
        <li class="todo" :class="{editing: todo === editing}" v-for="(todo, index) in filteredTodo" :key="index" >

          <input class="edit" type="text" 
            v-model="todo.name" 
            @keyup.enter="doneEdit"
            @keyup.esc="cancelEdit"
            v-focus="todo === editing"
            @blur="cancelEdit"> 

          <input type="checkbox" v-model="todo.completed">
          <label :class="{completed: todo.completed}" @dblclick="editTodo(todo)">{{ todo.name }}</label>
          <span @click.prevent="deleteTodo(todo)">delete</span>
        </li>
      </ul>
    </section>
    
    <footer v-show="hasTodos">
      <p> 
        <span class="todo-count">{{ remaining }}</span> 
        remaining tasks
      </p>

      <ul>
        <li><a href="#" :class="{selected: filters === 'all'}" @click.prevent="filters = 'all'">all</a></li>
        <li><a href="#" :class="{selected: filters === 'todo'}" @click.prevent="filters = 'todo'">to do</a></li>
        <li><a href="#" :class="{selected: filters === 'done'}" @click.prevent="filters = 'done'">done</a></li>
        <li><a href="" class="clear-all" v-show="completed" @click.prevent="deleteCompleted">delete completed</a></li>
      </ul>

    </footer>
  </section>
</template>

<script>
import Vue from 'vue';

export default {
  name: 'app-todo',

  data () {
    return {  
      todos: [{
        name: 'default task',
        completed: false
      }],
      newTodo: '',
      filters: 'all',
      editing: null,
      oldTodo: ''
    }
  },


  computed: {
    remaining() {
      return this.todos.filter(todo => !todo.completed).length;
    },

    completed() {
      return this.todos.filter(todo => todo.completed).length > 0;
    },

    hasTodos() {
      return this.todos.length > 0;
    },

    filteredTodo() {
      if(this.filters === 'todo') {
        return this.todos.filter(todo => !todo.completed);
      } else if (this.filters === 'done') {
        return this.todos.filter(todo => todo.completed);
      } else {
        return this.todos;
      }
    },

    allDone: {
      get() {
        return this.remaining === 0;
      },

      set(value) {
        this.todos.forEach(todo => {
          todo.completed = value;
        })
      }
    }
  },


  methods: {
    addTodo() {
      this.todos.push({
        name: this.newTodo,
        completed: false
      })
      this.newTodo = '';
    },

    editTodo(selectedTodo) {
      this.editing = selectedTodo;
      this.oldTodo = selectedTodo.name;
    },

    doneEdit() {
      this.editing = null;
    },

    cancelEdit() {
      this.editing.name = this.oldTodo;
      this.doneEdit();
    },

    deleteTodo(selectedTodo) {
      // plutôt réservé pour de l'arhivage car supprime pas la tâche du tableau
      this.todos = this.todos.filter(todo => todo != selectedTodo);
    },

    deleteCompleted() {
      this.todos = this.todos.filter(todo => !todo.completed);
    }
  },

  directives: {
    focus(el, value) {
      if(value) {
        Vue.nextTick(() => {
          el.focus();
        })
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss" src="./_app-todo-style.scss"></style>
