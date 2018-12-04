<template>
  <div class="card" @dragenter="dragEnterHandler" @dragleave="dragLeaveHandler" @dragover="dragOverHandler" @drop="dropHandler">
    <h3>{{ card.name }}</h3>
    <div class="cost-list" v-if="card.hasOwnProperty('cost')">
      <h4>Cost</h4>
      <ul>
        <li v-for="(value, key) in card.cost">{{ key }}: {{ value }}</li>
      </ul>
    </div>
    <div class="cost-list" v-if="card.hasOwnProperty('gain')">
      <h4>Gain</h4>
      <ul>
        <li v-for="(value, key) in card.gain">{{ key }}: {{ value }}</li>
      </ul>
    </div>
    <div class="cost-list" v-if="card.hasOwnProperty('requires')">
      <h4>Requirements</h4>
      <ul>
        <li v-for="requirement in card.requires">{{ requirement }}</li>
      </ul>
    </div>
    <div class="worker-container" v-if="card.player > -1">
      <worker :player="{player: card.player}" :index="card.player"></worker>
    </div>
  </div>
</template>

<script>
  import Worker from './Worker.vue'

  export default {
    name: 'card',
    created() {
    },
    data() {
      return {}
    },
    props: ['card', 'cardIndex'],
    components: {
      Worker
    },
    methods: {
      dropHandler: function (evt) {
        let data = evt.dataTransfer.getData('text/plain')
        let workerIndex = parseInt(data)
        this.$emit('worker-dropped', workerIndex, this.cardIndex)
        console.log('dropped', evt, workerIndex)
        evt.preventDefault()
        // console.log('dropped', evt, this.card)
      },
      dragEnterHandler: function (evt) {
        evt.preventDefault()
      },
      dragLeaveHandler: function (evt) {
        evt.preventDefault()
      },
      dragOverHandler: function (evt) {
        evt.preventDefault()
      }
    }
  }
</script>

<style>
  .card {
    border: 1px solid black;
    margin: 0.2em;
    padding: 0.2em;
    background: white;
    box-shadow: 0.1em 0.1em 0.1em;
  }

  .worker-container {
    position: relative;
    width: 6vw;
    height: 6vw;
  }

  .card h3 {
    margin-bottom: 0.2em;
  }

  .card h4 {
    margin-top: 0.2em;
  }

  .cost-list ul {
    margin-top: 0.1em;
    padding-inline-start: 1em;
  }

  .cost-list h4 {
    margin-bottom: 0.1em;
  }
</style>
