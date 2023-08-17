<template>
  <div class="container" v-if="showBlock" @click="stopTimer">
    <div class="block">Click me</div>
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
      console.log(this.reactionTime);
    },
  },
};
</script>

<style>
.container {
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0px 20px;
}

.block {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  max-width: 400px;
  height: 200px;
  text-align: center;
  border-radius: 20px;
  background: palevioletred;
  color: white;
  text-align: center;
}
</style>
