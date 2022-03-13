<template>
  <div class="result">
    Your result is {{ score }} ms<span></span>
    <div ref="color">Siz {{ rank }}siz !!!</div>
  </div>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score <= 260) {
      this.rank = "Chaqqon";
      this.$refs.color.style.color = "green";
    } else if (this.score < 360) {
      this.rank = "Ildam";
      this.$refs.color.style.color = "blue";
    } else {
      this.rank = "Qo'pol";
      this.$refs.color.style.color = "crimson";
    }
  },
};
</script>

<style>
.result {
  font-size: 24px;
  font-weight: bold;
  text-align: center;
  margin-top: 20px;
}
.result div {
  margin-top: 20px;
  color: crimson;
  font-weight: black;
}
</style>