<template>
  <div :class="{'player-one':(player.player === 0), 'player-two':(player.player === 1), 'player-status':true, 'player-active':(player.myTurn)}">
    <div class="sub-status">
      <h1 v-if="player.won">{{ player.name }} won!</h1>
      <h2>{{ player.name }} {{ (youAre) ? '<-- YOU' : '' }}  <small v-if="player.firstPlayer">First player</small></h2>
      <table>
        <tbody>
        <tr><td>Cash: </td><td>{{ player.cash }}</td></tr>
        <tr><td>Aluminum: </td><td>{{ player.aluminum }}</td></tr>
        <tr><td>Carbon fiber: </td><td>{{ player.carbon }}</td></tr>
        <tr><td>Electronics: </td><td>{{ player.electronics }}</td></tr>
        </tbody>
      </table>
      <small>{{ ((player.lastSeen === -1) ? 'Waiting for player' : 'Player last seen ' + secondsAgo + ' seconds ago.') }}</small>
    </div>
    <div class="sub-status">
      <rocket :rocket="player.rocket"></rocket>
    </div>
  </div>
</template>

<script>
  import Rocket from './Rocket.vue'

  export default {
    name: 'player-status',
    created () {
      console.log(this.player)
    },
    data () {
      return {
      }
    },
    props: ['player', 'youAre'],
    components: {
      Rocket
    },
    computed: {
      secondsAgo: function () {
        return Math.floor((Date.now() - this.player.lastSeen) / 1000)
      }
    }
  }
</script>

<style>
  .player-status {
    display: flex;
    flex-grow: 1;
    margin: 0;
    padding: 0.5em;
  }
  .player-one {
    background-color: teal;
  }
  .player-two {
    background-color: #d85619;
  }
  .player-active {
    box-sizing: border-box;
    border: 0.5em solid gold;
  }
  .player-status h2, h3 {
    margin-top: 0.2em;
  }
  .sub-status {
    flex-grow: 1;
  }
</style>
