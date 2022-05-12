<template>
<div id="app">

  <h1>Would You Rather?</h1>

  <would-you-rather v-for="question in questions"
                    v-bind:key="question"
                    v-bind:question="question.WEEK10Question"
                    v-bind:Answer1="question.WEEK10Answer1"
                    v-bind:Answer2="question.WEEK10Answer2"
                    v-on:option-changed="optionChanged"
  ></would-you-rather>

                     <p v-for="Answer in userSelectionMessage">{{Answer}}</p>
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
      questions: [
        {
          id: 0,
          WEEK10Question: 'Would you rather dance or sing?',
          WEEK10Answer1: 'Dance',
          WEEK10Answer2: 'Sing',
          userSelectionMessage: ''
        },
        {
          id: 1,
          WEEK10Question: 'Would you rather have the ability to see 10 minutes into the future or 150 years into the future?',
          WEEK10Answer1: 'See 10 minutes into the future',
          WEEK10Answer2: '150 years into future',
          userSelectionMessage: ''
        },
        {
          id: 2,
          WEEK10Question: 'Would you rather solve world hunger or global warming?',
          WEEK10Answer1: 'Solve world hunger',
          WEEK10Answer2: 'Solve global warming',
          userSelectionMessage: ''
        },
      ],
      userSelectionMessage: []
    }
  },
  methods:{
    optionChanged(choice){
    this.userSelectionMessage.push(`Thanks You chose ${choice}!`)
    }

  }
}
</script>

<style>

body{
  background: lavender;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 30px;
  background: darkgrey;
}
</style>
