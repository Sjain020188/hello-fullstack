<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>{{data}}</h1>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
export default {
  name: "app",
  components: {
    HelloWorld
  },

  data: () => ({
    data: null
  }),

  mounted() {
    fetch("/api")
      .then(data => {
        return data.text();
      })
      .then(x => (this.data = x));
    // axios.get("/api").then(res => {
    //   this.data = res.data;
    // });
  }
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
