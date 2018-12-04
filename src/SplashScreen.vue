<template>
  <div class="splash-screen">
    <img class="rocket-parts" src="./assets/rocket2-fins1.png">
    <img class="rocket-parts" src="./assets/rocket2-fins2.png">
    <img class="rocket-parts" src="./assets/rocket2-booster3.png">
    <img class="rocket-parts" src="./assets/rocket2-booster2.png">
    <img class="rocket-parts" src="./assets/rocket2-booster1.png">
    <img class="rocket-parts" src="./assets/rocket2-nosecone.png">
    <img class="rocket-parts" src="./assets/rocket2-cockpit.png">
    <img class="rocket-parts" src="./assets/title.png">
    <div
      class="instructions">
      <h1>Instructions</h1>
      <ul>
        <li>This is a multi-player game, try opening two windows at once.</li>
        <li>The first player who successfully launches a rocket wins.</li>
        <li>Drag and drop your workers to cards on your turn.</li>
        <li>Every turn new cards are added to the offer.</li>
        <li>Every 4th turn is payday, pay 2 cash for each worker or they are 'fired'.</li>
        <li>The more components you add to your rocket, the more likely it is to launch.</li>
        <li>If the launch fails, you'll lose the parts and the worker who launched it.</li>
        <li>Click 'Start game' to begin.</li>
      </ul>
    </div>
    <div
      class="start-button"
      @click="startGame">
      <h2>Start Game</h2>
    </div>
  </div>
</template>

<script>
export default {
  name: 'splash-screen',
  created () {
  },
  methods: {
    startGame: function () {
      this.$emit('start-game')
    }
  },
  data () {
    return {
    }
  }
}
</script>

<style>
  .start-button {
    background: #d85619;
    color: white;
    position: absolute;
    padding: 1em;
    top: 1em;
    left: 1em;
    cursor: pointer;
  }
  .splash-screen {
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
  .instructions {
    background: rgba(255, 255, 255, 0.8);
    position: absolute;
    right: 5px;
    bottom: 5px;
  }
</style>
