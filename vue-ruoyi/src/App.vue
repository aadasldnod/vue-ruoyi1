<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
import Login from "./components/Login"
export default {
  name: 'App',
  components: {
    Login
  }
}
</script>

<style>
@import "./assets/css/init.css"
</style>
