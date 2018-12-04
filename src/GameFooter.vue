<template>
  <div class="game-footer">
    <building v-if="youAre > -1 && players.length > youAre"
              :building="players[youAre].workers"
              :player="players[youAre]">
    </building>
    <calendar :upcoming-cards="upcomingCards"></calendar>
  </div>
</template>

<script>
  import Building from './Building.vue'
  import Calendar from './Calendar.vue'

  export default {
    name: 'game-footer',
    components: {
      Building,
      Calendar
    },
    props: ['players', 'upcomingCards', 'youAre']
  }
</script>

<style>
  .game-footer {
    flex-grow: 1;
    display: flex;
    background-color:peru;
  }
</style>
