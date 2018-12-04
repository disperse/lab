<template>
  <div class="cards">
    <card
      v-for="(card, index) in cards"
      v-on:worker-dropped="workerDropped"
      :card="card"
      :card-index="index"></card>
  </div>
</template>

<script>
  import Card from './Card.vue'

  export default {
    name: 'cards',
    created () {
    },
    data () {
      return {
      }
    },
    props: ['cards'],
    components: {
      Card
    },
    methods: {
      workerDropped(workerIndex, cardIndex) {
        console.log('workerDropped', workerIndex, cardIndex)
        this.$emit('worker-dropped', workerIndex, cardIndex)
      }
    }
}
</script>

<style>
  .cards {
    flex-wrap: wrap;
    flex-grow: 4;
    display: flex;
    background-color:#eee;
  }
</style>
