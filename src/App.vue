<template>
  <div id="app">
    <CountdownTimer />
  </div>
</template>

<script>
import CountdownTimer from './components/CountdownTimer.vue';

export default {
  components: {
    CountdownTimer,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
}
</style>
