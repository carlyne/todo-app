<template>
  <section class="todo">

    <header class="header">
      <h1>Todo</h1>
      <input type="text" class="new-todo" placeholder="Add a task"> 
    </header>

    <section class="main">
      <ul class="todo-list">
        <li class="todo">
          <label>Task's name</label>
        </li>
      </ul>
    </section>
    
  </section>
</template>

<script>
export default {
  name: 'todo'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

section.todo h1 {
  color: pink;
  font-size: 5rem;
  text-align: center;
  margin-bottom: 30px;
  padding: 5px;
}

section.todo li {
  display: inline-block;
  margin: 0;
  padding: 10px;
}

section.todo input {
  width: 100%;
  border: 2px solid grey;
  background: none;
  border-radius: 2px;
  font-size: inherit;
  color:inherit;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  margin: 0;
  padding: 10px;

  &::placeholder {
    font-style: normal;
    font-size: inherit;
    color:inherit;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    opacity: .3;
  }
}

section.todo .main  {
  width: 100%;

  & li {
    width: 100%;
    background: rgba(249, 208, 250, 0.5);
    border-radius: 2px;
    margin: 0;
    padding: 10px;
    font-size: inherit;
    color:inherit;

    
    & label {
      font-size: inherit;
      color: inherit;
      font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
      opacity: .8;
    }

  }

}
</style>
