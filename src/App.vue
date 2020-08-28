<template>
  <div id="app">
    <br />
    <img class="rounded-circle" src="" width="20%" />
    <HelloWorld msg="" />
    <br />
    <h1 class="text-light"></h1>
    <div>
      <botton />
    </div>
  </div>
</template>
<script>
import HelloWorld from "./components/HelloWorld.vue";
import botton from "./components/botton.vue";
export default {
  name: "App",
  components: {
    HelloWorld,
    botton,
  },
};
</script>

<style>
#app {
  background-image: url(https://i.gifer.com/224C.gif);
  background-size: 200%;
  background-size: cover;
  
  
  font-family: 'Courier New', Courier, monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color:lightgreen;
}
</style>
