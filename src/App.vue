<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
const fileType = require('file-type');


export default {
  name: "app",
  components: {
    HelloWorld,
  },
  mounted() {
    const xhr = new XMLHttpRequest();
    xhr.open("GET", "/mylogo.png");
    xhr.responseType = "arraybuffer";

    xhr.onload = () => {
      console.log("file-type", fileType(new Uint8Array(this.response)));
      //=> {ext: 'png', mime: 'image/png'}
    };

    xhr.send();
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
