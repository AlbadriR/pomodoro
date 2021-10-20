<template>
  <div class="buttons">
    <button class="btnPlay" @click="play" id="idPlay" :disabled="isPlayed"></button>
    <button class="btnPause" @click="pause" id="idPause" :disabled="isPaused"></button>
    <button class="btnStop" @click="stop" id="idStop" :disabled="isStoped"></button>
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
      minute: 1,
      seconde: 0,
      isPausedStarted: false,
    };
  },
  props: [''],
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
      this.isPausedStarted = false;
      this.isPlayed = false;
      this.isPaused = true;
      this.isStoped = true;
      this.minute = 20;
      this.seconde = 0;
    },
    timer() {
      if (this.minute != 0 || this.seconde != 0) {
        if (this.seconde == 0) {
          this.minute -= 1;
          this.seconde = 59;
        } else {
          this.seconde -= 1;
        }
      }
      else{
        this.isPlayed = false;
        this.isPausedStarted = true;
      }
    },
  },
};
//v-bind:style="{ backgroundImage: 'url(../assets/play.png)'}"
</script>



<style>
.timer {
  display: flex;
  flex-direction: column;
}

.buttons {
  display: flex;
  justify-content: center;
  margin-top: 30px;
  margin-bottom: 30px;
}

.btnPlay {
  background-image: url("../../img/play.png");
  width: 50px;
  height: 50px;
  background-size: cover;
  margin-right: 10px;
}
.btnPause {
  background-image: url("../../img/pause.png");
  width: 50px;
  height: 50px;
  background-size: cover;
}
.btnStop {
  background-image: url("../../img/stop.png");
  width: 50px;
  height: 50px;
  background-size: cover;
  margin-left: 10px;
}
</style>
