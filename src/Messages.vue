<template>
  <div class="upcoming-cards">
    <h3>Game log</h3>
    <div class="messages">
      <ul>
        <li v-for="message in messages">{{ message }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'messages',
    created () {
    },
    data () {
      return {
      }
    },
    components: {
    },
    props: ['messages']
}
</script>

<style>
  .upcoming-cards {
    border: 1px solid black;
    padding: 1em;
  }
  .messages {
    display: flex;
    flex-grow: 1;
  }
</style>
