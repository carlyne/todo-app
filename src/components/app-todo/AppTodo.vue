<template>
  <section class="todo">

    <header>
      <h1>Todo</h1>
      <input type="text" class="new-todo" placeholder="Add a task" v-model="newTodo" @keyup.enter="addTodo"> 
    </header>

    <section class="main">
      <ul class="todo-list">
        <li class="todo" v-for="todo in todos" :key="todo.name">
          <input type="checkbox" v-model="todo.completed">
          <label :class="{completed: todo.completed}">{{ todo.name }}</label>
        </li>
      </ul>
    </section>
    
    <footer>
      <p> 
        <span class="todo-count">{{ remaining }}</span> 
        Tâches à faires
      </p>

      <ul>
        <li><a href="#">Toutes</a></li>
        <li><a href="#">à faire</a></li>
        <li><a href="#">faites</a></li>
      </ul>

    </footer>
  </section>
</template>

<script>
export default {
  name: 'app-todo',

  data () {
    return {
      todos: [{
        name: 'tache de test',
        completed: false
      }],
      newTodo: ''
    }
  },

  computed: {
    remaining() {
      return this.todos.filter(todo => !todo.completed).length;
    }
  },

  methods: {
    addTodo() {
      this.todos.push({
        name: this.newTodo,
        completed: false
      })
      this.newTodo = '';
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss" src="./_app-todo-style.scss"></style>
