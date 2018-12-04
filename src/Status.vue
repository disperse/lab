<template>
  <div class="status">
    <player-status :youAre="youAre === 0" :player="players[0]"></player-status>
    <player-status :youAre="youAre === 1" :player="players[1]"></player-status>
  </div>
</template>

<script>
  import PlayerStatus from './PlayerStatus.vue'

  export default {
    name: 'status',
    data () {
      return {
      }
    },
    props: ['players', 'youAre'],
    components: {
      PlayerStatus
    }
}
</script>

<style>
  .status {
    flex-grow: 2;
    display: flex;
  }
</style>
