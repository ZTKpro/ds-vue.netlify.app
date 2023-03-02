<template>
  <div class="app">
    <my-button color="primary" @click="onClick">Click me!</my-button>
  </div>
</template>

<script>
import MyButton from "./components/MyButton.vue";

export default {
  name: "App",
  components: {
    MyButton,
  },
  methods: {
    onClick() {
      alert("Button clicked!");
    },
  },
};
</script>


<style>
/* Global Styles */

body {
  min-height: 100vh;
  margin: 0;
  padding: 0;
  font-family: "Roboto", sans-serif;
  background-image: url("./components/bg.png");
  background-size: cover;
}

.app {
  text-align: center;
  padding: 100px 0;
}
</style>