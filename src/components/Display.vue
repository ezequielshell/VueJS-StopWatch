<template>
  <div>
    <div class="stopwatch">
      <div class="screenWatch">
        <input type="number" placeholder="0" v-model="hours" />
        <input type="number" placeholder="0" v-model="minutes" />
        <input type="number" placeholder="0" v-model="seconds" />
      </div>
    </div>
    <div v-if="!counting" class="sendButton">
      <button @click="handleTimer">Set</button>
    </div>
    <div v-else class="pauseButton">
      <button @click="pauseTimer">Pause</button>
    </div>
  </div>
</template>
<script>
export default {
  name: "Display",

  data() {
    return {
      hours: null,
      minutes: null,
      seconds: null,

      counting: false,
      timerInterval: null,
    };
  },
  methods: {
    handleTimer() {
      this.counting = true;

      this.timerInterval = setInterval(() => {
        this.handleSeconds();
      }, 1000);
    },

    handleSeconds() {
      if (this.seconds >= 60) {
        this.seconds = 60;
      }
      if (this.minutes >= 60) {
        this.minutes = 59;
      }

      if (!this.seconds && !this.minutes && !this.hours) {
        clearInterval(this.timerInterval);
        this.seconds = null;
        this.minutes = null;
        this.counting = false;
        return;
      }

      if (!this.seconds && this.minutes) {
        this.minutes--;
        this.seconds = 60;
      }

      if (!this.seconds && !this.minutes && this.hours) {
        this.hours--;
        this.minutes = 59;
        this.seconds = 60;
      }

      this.seconds--;
    },

    handleMinutes() {
      this.minutes--;
    },

    pauseTimer() {
      clearInterval(this.timerInterval);
      this.counting = false;
    },
  },
};
</script>

<style>
.stopwatch {
  display: flex;
  justify-content: center;
}

.stopwatch .screenWatch {
  display: flex;
  align-items: center;
  height: 350px;
  width: 350px;
  padding: 70px;
  border-radius: 50%;
  border: 4px solid #c57b57;
}

.stopwatch input {
  font-size: 50px;
  font-family: "Montserrat-Light";
  color: #fff;
  width: 30%;
  border: 0;
  text-align: end;
}

::placeholder {
  color: #fff;
}

.sendButton,
.pauseButton {
  margin-top: 50px;
}

button {
  font-family: "Montserrat-Regular";
  font-size: 20px;
  border: 0;
  background-color: #519872;
  padding: 20px;
  border-radius: 15px;
  width: 150px;
  color: #fff;
  font-weight: bold;
}

button:hover {
  background-color: #346049;
}
</style>
