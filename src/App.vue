<template>
  <div id="app">
    <SignupForm />
  </div>
</template>
<!-- github branch: lessson44 -->
<!-- (https://github.com/iamshaunjp/Vue-3-Firebase/blob/lesson-44/web-forms/src/App.vue) -->

<script>
import SignupForm from "./components/SignupForm";
export default {
  name: "App",
  components: { SignupForm },
};
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
body {
  margin: 0;
  background: #eee;
}
</style>
