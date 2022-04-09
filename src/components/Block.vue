<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click Me</div>
</template>

<script>
export default {
  props: ["delay"],
  emits: ["end"],
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
    },
  },
};
</script> 

<style scoped>
.block {
  max-width: 400px;
  border-radius: 20px;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;

  background: #00a28a;
  color: #fff;
  font-weight: 600;
}
</style>