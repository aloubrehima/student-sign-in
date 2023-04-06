<template>
  <div id="app">
   
    <h1>Would You Rather??</h1>

    <would-you-rather v-bind:question="wyrQuestion"
    v-bind:answer1="wyrAnswer1"
    v-bind:answer2="wyrAnswer2"
    v-on:answer-modified="answerModified"></would-you-rather>


    <p>{{  userSelectionMessage }}</p>
  </div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() {
    return {
      wyrQuestion:'Would you rather be able to play the piano or the guitar?',
      wyrAnswer1:'Piano',
      wyrAnswer2:'Guitar',
      userSelectionMessage:''
    }
  },
  methods: {
    answerModified(choice) {
      this.userSelectionMessage='Thanks! You chose ${choice}'
    }
  }
}
</script>


<style>

body {
  background:orange;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
