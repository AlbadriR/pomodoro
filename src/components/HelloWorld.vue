<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <img
      class="Coin"
      style="width:20vh"
      alt="Vue logo"
      src="../../img/Tomato.png"
    />
  </div>
</template>

<script>
export default {
  name: "Header",
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@keyframes CoinAnim {
  from {
    transform: rotateY(0deg);
  }
  to {
    transform: rotateY(360deg);
  }
}

.Coin {
  width: 10vw;
  height: 10vw;
  animation: CoinAnim 15s infinite;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
