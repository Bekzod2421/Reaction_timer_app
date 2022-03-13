<template>
  <div class="block" v-if="bShow" @click="timer">Click Me</div>
</template>
<script>
export default {
  props: ["delay"],
  data() {
    return {
      bShow: false,
      time: null,
      farq: 0,
    };
  },
  methods: {
    startT() {
      this.time = setInterval(() => {
        this.farq += 10;
      }, 10);
    },
    timer() {
      clearInterval(this.time);
      this.$emit("end", this.farq);
    },
  },
  mounted() {
    setTimeout(() => {
      this.bShow = true;
      this.startT();
    }, this.delay);
  },
  updated() {
    //  console.log(this.farq);
  },
  unmounted() {},
};
</script>


<style>
.block {
  width: 400px;
  height: 200px;
  background-color: blueviolet;
  margin: 20px auto;
  line-height: 200px;
  color: #fff;
  font-size: 24px;
  text-transform: uppercase;
  font-weight: bold;
  cursor: pointer;
}
</style>