<template>
  <div id="app">
    <div id="nav">
      <router-link to="/"></router-link> 
      <router-link to="/about"></router-link>
    </div>
    <router-view/>
  </div>
</template>

<style lang="scss">
#app {
  text-align: center;
}
</style>

<script>
import './assets/tailwind.css'
export default {
  
}
</script>
