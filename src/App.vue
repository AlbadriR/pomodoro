<template>
  <HelloWorld msg="Pomodoro : Rami"/>
  <Item ></Item>
  <Cat v-if="isPausedStarted" ref="coucou"></Cat>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import Item from "./components/Item.vue";
import Cat from "./components/Cat.vue";

export default {
  name: 'App',
  components: {
    HelloWorld,
    Item,
    Cat,
  },

  methods: {
    LoadCat() {
      this.$refs.coucou.loadNextImage()
    } 
  },
  updated() {
    setInterval(() => {
		this.LoadCat()
	}, 3000)
     
    
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
