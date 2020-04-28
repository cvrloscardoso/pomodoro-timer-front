<template>
  <div id="app">
    <pageHeader />
    <timer />
    <tasks />
  </div>
</template>

<script>
import pageHeader from './components/pageHeader.vue';
import Timer from './components/Timer.vue';
import Tasks from './components/Tasks.vue';

export default {
  name: 'App',
  components: {
    pageHeader,
    Timer,
    Tasks
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
