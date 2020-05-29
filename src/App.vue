<template>
  <main id="app">
    <router-view/>
  </main>
</template>

<style lang="scss">

* {
  box-sizing: border-box;
}

body {
  color: #222;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  margin: 0 auto;
  padding: 0;
  display: flex;
  justify-content: center;

}

main {
  min-width: 100%;
  margin: auto;
  padding: 50px;

  @media (min-width: 48rem) {
    min-width: 50%;
  }
}

ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

a {
  text-decoration: none;
  color: inherit;
}

</style>
