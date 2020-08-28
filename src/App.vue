<template>
  <div id="app">
    <main-bar></main-bar>
    <router-view></router-view>
  </div>
</template>

<script>
import mainBar from './components/content/mainTabbar/mainBar'
export default {
  name: 'App',
  components: {
    mainBar
  }
}
</script>

<style>
  @import 'assets/css/base.css'
</style>
