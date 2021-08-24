<template>
  <div id="app">
    <Header :name="fullName"/>
    <Github/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Github from './components/Github.vue'
import 'normalize.css'

export default {
  name: 'App',
  components: {
    Header,
    Github,
  },
  data() {
  return {
    firstName: "Jestin",
    lastName: "Mounts"
  }
  },
  computed: {
    fullName() {
      return `${this.firstName} ${this.lastName}`;
    }
  },
}
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}
</style>
