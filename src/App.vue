<template>
  <div class="wrap">
    <h1>Bekzod's Reaction Timer App</h1>
    <button class="test" @click="blockShow" :disabled="bShow">Play</button>
    <Block v-if="bShow" :delay="delay" @end="endGame" />
    <Result v-if="rShow" :score="score" />
  </div>
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  components: {
    Block,
    Result,
  },
  data() {
    return {
      bShow: false,
      rShow: false,
      delay: null,
      score: 0,
    };
  },
  methods: {
    blockShow() {
      this.delay = 2000 + Math.random() * 1000;
      this.bShow = true;
      this.rShow = false;
    },
    endGame(score) {
      this.score = score;
      this.bShow = false;
      this.rShow = true;
    },
  },
};
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
.wrap {
  max-width: 1400px;
  margin: 0 auto;
}
.test {
  font-size: 24px;
  text-transform: uppercase;
  display: inline-block;
  cursor: pointer;
  background-color: crimson;
  color: #fff;
  border: none;
  padding: 15px 20px;
  border-radius: 15px;
}
.test:disabled {
  background-color: grey;
  cursor: not-allowed;
  opacity: 60%;
}
</style>
