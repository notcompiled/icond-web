<template>
  <div id="app">
    <v-app-bar id="nav">
      <v-app-bar-nav-icon/>
    </v-app-bar>
    <router-view/>
  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  background-color: #40A798;

  a {
    font-weight: bold;
    color: #40A798;

    &.router-link-exact-active {
      color: #000000;
    }
  }
}
</style>
