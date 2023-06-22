<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/sobre">Pijas</router-link>
    </nav>
    <router-view/>
  </div>
</template>

<style>

*{
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
  background-color: #f5f5f5;
}

nav a {
  font-weight: bold;
  color: #1C1C1C;
}

nav a.router-link-exact-active {
  color: #42b983;
}

</style>
