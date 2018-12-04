<template>
  <div id="app">
    <splash-screen
      v-if="!gameStarted"
      v-on:start-game="startGame">
    </splash-screen>
    <status v-if="gameStarted && game.players.length > 0" :you-are="game.youAre" :players="game.players"></status>
    <cards
      v-if="gameStarted && game.activeCards.length > 0"
      :cards="game.activeCards"
      v-on:worker-dropped="workerDropped">
    </cards>
    <game-footer
      v-if="gameStarted"
      :you-are="game.youAre"
      :players="game.players"
      :upcoming-cards="game.upcomingCards">
    </game-footer>
  </div>
</template>

<script>
  import SplashScreen from './SplashScreen.vue'
  import Status from './Status.vue'
  import Cards from './Cards.vue'
  import GameFooter from './GameFooter.vue'
  import Request from 'axios-request-handler'
  import http from 'axios'
  import backgroundMusic from './assets/background-song.m4a'
  import uuid from 'uuid/v4'

  const POLLING_DELAY = 5000
  // const SERVER_URL = 'http://localhost:5000/game/' // dev
  const SERVER_URL = 'https://cryptic-wave-46600.herokuapp.com/game/' // prod

  export default {
    name: 'app',
    created () {
    },
    data () {
      return {
        gameStarted: false,
        game: {
          youAre: -1,
          players: [],
          activeCards: [],
          upcomingCards: []
        }
      }
    },
    components: {
      SplashScreen,
      Status,
      Cards,
      GameFooter
    },
    methods: {
      startGame: function() {
        this.gameStarted = true
        const music = new Audio(backgroundMusic)
        music.loop = true
        music.play()

        if (window.location.search.length === 0) {
          window.location.search = uuid()
          // this.$router.push({query: {userId: uuid()}})
        }

        let userId = window.location.search.substr(1)
        let url = SERVER_URL + userId
        console.log('url', url)
        const requestInstance = new Request(url)
        requestInstance.poll(POLLING_DELAY).get((response) => {
          this.game = response.data
          window.youAre = response.data.youAre
          console.log(this.game)
        })
      },
      workerDropped: function(workerIndex, cardIndex) {
        console.log('App: workerDropped', workerIndex, cardIndex)
        let userId = window.location.search.substr(1)
        let url = SERVER_URL + userId
        http.post(url, {
          'workerIndex':workerIndex,
          'cardIndex':cardIndex
        }).then((res) => {
          this.game = res.data
        })
      }
    }
  }
</script>

<style>
  #app {
    display: flex;
    flex-direction: column;
    padding: 0;
    margin: 0;
    font-family: 'VT323', monospace;
    text-rendering: optimizeSpeed;
    height: 100vh;
  }
  body, html {
    padding: 0;
    margin: 0;
  }
  img {
    image-rendering: pixelated;
  }
</style>
