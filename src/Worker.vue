<template>
  <div
    :class="{'worker':true, 'player-one':(player.player === 0), 'player-two':(player.player === 1)}"
    draggable="true" @dragstart="dragWorker" @dragend="dragEnd">
    <img class="worker-image" src="./assets/worker.png">
  </div>
</template>

<script>
  export default {
    name: 'worker',
    created() {
    },
    data() {
      return {}
    },
    props: ['player', 'index'],
    components: {},
    methods: {
      dragWorker: function (ev) {
        console.log('dragWorker', ev)
        ev.dataTransfer.setData('text/plain', this.index)
      },
      dragEnd: function (ev) {
        console.log('dragEnd', ev)
      }
    }
  }
</script>

<style>
  .worker {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    position: absolute;
    top: 0;
    left: 0;
    cursor: grab;
  }
  .player-one {
    background-color: teal;
  }
  .player-two {
    background-color: #d85619;
  }
  .worker-image {
    height: 100%;
    max-width: 100%;
    max-height: 100%;
    display: block;
    margin: auto;
  }
</style>
