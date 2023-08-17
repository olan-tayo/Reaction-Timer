<template>
  <p class="time">Reaction Time - {{ reactionTime }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ["reactionTime"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.reactionTime < 250) {
      this.rank = "Fast Fingers";
    } else if (this.reactionTime < 400) {
      this.rank = "Rapid Reflexes";
    } else {
      this.rank = "Snail pace...";
    }
  },
};
</script>

<style scoped>
.time {
  margin-top: 15px;
  font-weight: 400;
  font-size: 15px;
  letter-spacing: 0.34px;
}

.rank {
  font-size: 18px;
  letter-spacing: 0.4px;
  color: palevioletred;
  font-weight: 500;
  margin-top: 10px;
}
</style>
