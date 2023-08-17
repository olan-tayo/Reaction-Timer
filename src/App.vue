<template>
  <div>
    <h1>Reaction Timer</h1>

    <button @click="start" :disabled="isPlaying">Play</button>

    <Block v-if="isPlaying" :delay="delay" @end="endGame" />

    <Results v-if="showResults" :reactionTime="reactionTime" />
  </div>
</template>

<style scoped>
div {
  text-align: center;
  padding: 25px 0px;
}

h1 {
  color: black;
}

button {
  margin-top: 30px;
  padding: 8px 30px;
  outline: none;
  background-color: palevioletred;
  color: white;
  border: none;
  cursor: pointer;
  border-radius: 5px;
}

button:disabled {
  background-color: #ebebe4;
  color: black;
  cursor: not-allowed !important;
}
</style>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
export default {
  name: "App",
  data() {
    return {
      isPlaying: false,
      delay: null,
      reactionTime: 0,
      showResults: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.showResults = false;
      this.isPlaying = true;
    },
    endGame(reactionTime) {
      this.reactionTime = reactionTime;
      this.showResults = true;
      this.isPlaying = false;
    },
  },
  components: {
    Block,
    Results,
  },
};
</script>
