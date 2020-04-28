<template>
  <div id="app">
    <pageHeader />
      <br />
      <br />
    <timer />
      <br />
      <br />
    <tasks />
  </div>
</template>

<script>
import PageHeader from './components/PageHeader.vue';
import Timer from './components/Timer.vue';
import Tasks from './components/Tasks.vue';

export default {
  name: 'App',
  components: {
    PageHeader,
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
