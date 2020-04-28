<template>
  <div class="timer-container">
    <h1> {{ title }}</h1>
    <h4> {{ subtitle }} </h4>

    <div class="timer">
      <span class="timer-minutes">{{ minutes }}</span>
      <span class="timer-middle">:</span>
      <span class="timer-seconds">{{ seconds }}</span>
    </div>

    <div class="btn-container">
      <button class="btn btn-success" v-if="!timer" @click="startTimer">
        Start
      </button>
      <button class="btn btn-warning" v-if="timer" @click="stopTimer">
        Pause
      </button>
      <button class="btn btn-danger" v-if="resetButton" @click="resetTimer">
        Stop
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "Pomodoro Timer",
      subtitle: "Powered by akc",
      timer: null,
      totalTime: (25 * 60),
      resetButton: false
    }
  },
  computed: {
    minutes: function() {
      const minutes = Math.floor(this.totalTime / 60);
      return this.padTime(minutes);
    },
    seconds: function() {
      const seconds = this.totalTime - (this.minutes * 60);
      return this.padTime(seconds);
    }
  },
  methods: {
    startTimer: function() {
      this.timer = setInterval(() => this.countdown(), 1000);
      this.resetButton = true;
    },
    stopTimer: function() {
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = true;
    },
    resetTimer: function() {
      this.totalTime = (25 * 60);
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = false;
    },
    padTime: function(time) {
      return (time < 10 ? '0' : '') + time;
    },
    countdown: function() {
      this.totalTime--;
    }
  },
}
</script>
<style scoped>
  .btn-container {
    margin: 10px;
  }
  .btn {
    margin: 0px 10px;
  }
  .timer {
    font-size: 50px;
    font-weight: bold;
  }
</style>
