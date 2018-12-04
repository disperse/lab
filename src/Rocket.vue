<template>
  <div class="rocket-status">
    <img v-if="rocket[6] === 1" class="rocket-parts" src="./assets/rocket2-fins1.png">
    <img v-if="rocket[5] === 1" class="rocket-parts" src="./assets/rocket2-fins2.png">
    <img v-if="rocket[4] === 1" class="rocket-parts" src="./assets/rocket2-booster3.png">
    <img v-if="rocket[3] === 1" class="rocket-parts" src="./assets/rocket2-booster2.png">
    <img v-if="rocket[2] === 1" class="rocket-parts" src="./assets/rocket2-booster1.png">
    <img v-if="rocket[1] === 1" class="rocket-parts" src="./assets/rocket2-nosecone.png">
    <img v-if="rocket[0] === 1" class="rocket-parts" src="./assets/rocket2-cockpit.png">
    <span class="success">Launch Success: {{ launchSuccess }}%</span>
  </div>
</template>

<script>
export default {
  name: 'rocket',
  created () {
    console.log(this.rocket)
  },
  data () {
    return {
    }
  },
  props: ['rocket'],
  computed: {
    launchSuccess: function () {
      if (this.rocket[0] === 0 || this.rocket[2] === 0) {
        return 0
      }
      let success = 15
      success += (this.rocket[1] + this.rocket[3] + this.rocket[4] + this.rocket[5] + this.rocket[6]) * 15
      return success
    }
  }
}
</script>

<style>
  .success {
    background-color: white;
    padding: 0.1em;
    position: absolute;
    bottom: 0.1em;
    right: 0.1em;
  }
  .rocket-status {
    width: 100%;
    height: 100%;
    position: relative;
  }
  .rocket-parts {
    height: 100%;
    max-width: 100%;
    max-height: 100%;
    position: absolute;
    top: 0;
    left: 0;
  }
</style>
