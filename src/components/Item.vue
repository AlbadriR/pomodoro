<template>
  <div class="buttons">
    <button @click="play" id="idPlay" :disabled="isPlayed">Play</button>
    <button @click="pause" id="idPause" :disabled="isPaused">Pause</button>
    <button @click="stop" id="idStop" :disabled="isStoped">Stop</button>
  </div>
  <div class="timer">
    <label v-show="isPlayed" id="lblEtat">WORK !</label>
    <label v-show="!isPlayed" id="lblEtat">REST !</label>
    <label>{{ minute }} : {{ seconde }}</label>
  </div>
</template>
<script>
export default {
  data() {
    return {
      isPlayed: false,
      isPaused: true,
      isStoped: true,
      minute: 20,
      seconde: 0,
    };
  },
  props: ["buttons"],
  methods: {
    play() {
      console.log(!this.isDisabled);
      this.isPlayed = true;
      this.isPaused = false;
      this.isStoped = false;
      if (this.minute > 0) {
        this.interval = setInterval(() => this.timer(), 1000);
      }
    },
    pause() {
      clearInterval(this.interval);
      this.isPlayed = false;
      this.isPaused = true;
      this.isStoped = false;
    },
    stop() {
      clearInterval(this.interval);
      this.isPlayed = false;
      this.isPaused = true;
      this.isStoped = true;
      this.minute = 20;
      this.seconde = 0;
    },
    timer() {
      if (this.minute > 0) {
        if (this.seconde == 0) {
          this.minute -= 1;
          this.seconde = 59;
        } else {
          this.seconde -= 1;
        }
      }
    },
  },
};
</script>

<style>
.timer {
  display: flex;
  flex-direction: column;
}

.buttons {
  display: flex;
  justify-content: center;
}
</style>
