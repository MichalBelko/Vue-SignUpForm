<template>
  <SignupForm />
</template>

<script>
import SignupForm from "./components/SignupForm.vue";

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
  max-width: 500px;
  display: block;
  margin: 0 auto;
}
body {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  background-color: #eee;
  overflow-x: hidden;
  overflow-y: hidden;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  align-content: center;
}
/* ---- reset ---- */
canvas {
  display: block;
  vertical-align: bottom;
} /* ---- particles.js container ---- */
#particles-js {
  position: absolute;
  width: 100vw;
  height: 100vh;
  top: 0;
  left: 0;
  background-color: #b61924;
  background-image: url("");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 50% 50%;
}
</style>
