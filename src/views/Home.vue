<template>
  <div class="home">
    <app-todo/>
  </div>
</template>

<script>
// @ is an alias to /src
import AppTodo from '@/components/app-todo/AppTodo.vue'

export default {
  name: 'Home',
  components: {
    AppTodo
  }
}
</script>
