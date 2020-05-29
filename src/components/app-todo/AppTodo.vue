<template>
  <section class="todo">

    <header>
      <h1>Todo</h1>
      <input type="text" class="new-todo" placeholder="Add a task" v-model="newTodo" @keyup.enter="addTodo"> 
    </header>

    <section class="main">
      <ul class="todo-list">
        <li class="todo" v-for="todo in filteredTodo" :key="todo.name">
          <input type="checkbox" v-model="todo.completed">
          <label :class="{completed: todo.completed}">{{ todo.name }}</label>
        </li>
      </ul>
    </section>
    
    <footer>
      <p> 
        <span class="todo-count">{{ remaining }}</span> 
        remaining tasks
      </p>

      <ul>
        <li><a href="#" :class="{selected: filters === 'all'}" @click.prevent="filters = 'all'">all</a></li>
        <li><a href="#" :class="{selected: filters === 'todo'}" @click.prevent="filters = 'todo'">to do</a></li>
        <li><a href="#" :class="{selected: filters === 'done'}" @click.prevent="filters = 'done'">done</a></li>
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
        name: 'default task',
        completed: false
      }],
      newTodo: '',
      filters: 'all'
    }
  },

  computed: {
    remaining() {
      return this.todos.filter(todo => !todo.completed).length;
    },

    filteredTodo() {
      if(this.filters === 'todo') {
        return this.todos.filter(todo => !todo.completed);
      } else if (this.filters === 'done') {
        return this.todos.filter(todo => todo.completed);
      } else {
        return this.todos;
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
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss" src="./_app-todo-style.scss"></style>
