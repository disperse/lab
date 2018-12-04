<template>
  <div class="upcoming-cards">
    <h3>Upcoming cards</h3>
    <div class="calendar">
      <card v-for="card in upcomingCards" :card="card"></card>
      <card :card="{'name':'Payday!', 'requires':['2 cash per worker']}"></card>
    </div>
  </div>
</template>

<script>
  import Card from './Card.vue'

  export default {
    name: 'calendar',
    created () {
    },
    data () {
      return {
      }
    },
    components: {
      Card
    },
    props: ['upcomingCards']
}
</script>

<style>
  .upcoming-cards {
    border: 1px solid black;
    padding: 1em;
  }
  .calendar {
    display: flex;
    flex-grow: 1;
  }
</style>
