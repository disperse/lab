<template>
  <div class="office-div">
    <h3>The L.A.B.</h3>
    <div class="building">
      <div v-for="(office, index) in building" class="office">
        <span v-if="office === 1 || office === 2 || office === 3">
          <img class="office-image" src="./assets/office.png">
          <span class="office-label">{{ (office === 1) ? 'Empty office' : 'Office' }}</span>
          <worker v-if="office === 2" :player="player" :index="index"></worker>
        </span>
        <span v-else>
          <img class="office-image" src="./assets/blueprints.png">
          <span class="office-label">Not built yet</span>
        </span>
      </div>
    </div>
  </div>
</template>

<script>
  import Worker from './Worker.vue'

  export default {
    name: 'building',
    created() {
      console.log('building', this.building)
    },
    data() {
      return {}
    },
    props: ['building', 'player'],
    components: {
      Worker
    }
  }
</script>

<style>
  .office-div {
    border: 1px solid black;
    border-right: none;
    padding: 1em;
  }

  .office-image {
    height: 100%;
    max-width: 100%;
    max-height: 100%;
  }

  .office-label {
    position: absolute;
    top: 0.1em;
    left: 0.1em;
    color: black;
    background: white;
  }

  .office {
    position: relative;
    width: 10vmin;
    height: 10vmin;

    border: 1px solid white;
    color: white;
  }

  .building {
    flex-wrap: wrap;
    flex-grow: 1;
    display: flex;
    background-color: #5051d2;
  }
</style>
