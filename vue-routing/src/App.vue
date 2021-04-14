<template>
  <div id="app">
    <b-navbar toggleable="lg" type="dark" variant="dark">
    <b-navbar-nav id='nav'>
        <b-nav-item><router-link to="/">Home</router-link></b-nav-item>
        <b-nav-item><router-link to="/about">About</router-link></b-nav-item>
        <b-nav-item><router-link to="/profile">Profile</router-link></b-nav-item>
        <b-nav-item><router-link to="/dashboard">Dashboard</router-link></b-nav-item>
      </b-navbar-nav>
    </b-navbar>
    <div>
      <Sidebar />
      <router-view />
    </div>
  </div>
</template>

<script>
import Sidebar from '@/components/Sidebar.vue';

export default {
  name: 'App',
  components: {
    Sidebar,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

/* #nav {

a{
  font-weight: bold;
  color: whitesmoke;
  text-decoration: none;

&.router-link-exact-active {
color: #42b983;
}
}
} */
</style>
