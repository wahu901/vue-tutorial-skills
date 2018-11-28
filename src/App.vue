<template>
  <div id="app">
    <!--
    <Skills msg="Welcome to Your Vue.js App"/>
    -->
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </nav>
    <router-view/>
  </div>
</template>

<script>
import Skills from './components/Skills.vue'

export default {
  components: {
    Skills
  }
}
</script>

<style>
body {
  background-color : #eeeeee
}

body, html {
  margin: 0;
  height: 100%;
}
/*
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
*/

nav {
  padding: 20px 20px 20px 0;
}

nav a{
  padding: 10px;
  text-decoration: none;
  background: #fff;
  border-radius: 3px;
  color: rgb(0,110,255);
  font-weight: bold;
  margin-right: 15px;
}
</style>
