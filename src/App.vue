<template>
  <HelloWorld msg="Pomodoro : Rami"/>
  <img style="width:20vh" alt="Vue logo" src="../img/Tomato.png">
  <Item/>
  <Etat etat=""/>
  <Timer time=""/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import Item from "./components/Item.vue";
import Timer from "./components/Timer.vue";
import Etat from "./components/Etat.vue";

export default {
  name: 'App',
  components: {
    HelloWorld,
    Item,
    Timer,
    Etat,
  },
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
