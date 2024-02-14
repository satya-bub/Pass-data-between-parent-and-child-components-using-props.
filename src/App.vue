<!-- App.vue -->
<template>
  <div id="app">
    <QuizBuilder />
  </div>
</template>

<script>
import QuizBuilder from './components/QuizBuilder.vue';

export default {
  components: {
    QuizBuilder,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h2 {
  color: #3498db;
}

h3 {
  color: #e74c3c;
}
</style>
