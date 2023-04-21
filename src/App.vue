<template>
    <div id="App">
  
      <h1> Would You Rather?</h1> 
      
      <would-you-rather v-bind:key="question.id" 
        v-for="question in questions"
        v-bind:id="question.id"
        v-bind:question="question.wyrQuestion"
        v-bind:answer1="question.wyrAnswer1"
        v-bind:answer2="question.wyrAnswer2"
        v-on:answer-changed="answerChanged">
        </would-you-rather> 
      
      <div id="results">
      <!-- this will be the header of the results-->
      <h1 > You would rather ... </h1>
      <!-- this will be shown before the list of user choices-->
      <p id="userSelection" v-show="!choices"> Try Making a selection above?</p> 
      
      <!--- create list of user choices for the qustions-->
        <ul id='userAnswer'>
        <li v-for="message in userSelectionMessages" v-bind:key="message"> 
          {{ message }}</li>
        </ul>
      </div>
    </div>

</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default { 
  name: 'App',
  components: {
    WouldYouRather
  },

  data(){
    return{
      // array of questions object, threeor more questions
      //each question object has an id, we'll have 3 wouldyourather
      //components and each will emit a message when the user makes choice
      //so if we give each coby of wouldyourather a unique ID,then
      //that component can include the ID when it emit a message
      //and  app.vue will be able to tell which component emitted that message.
      questions: [ 
        {
          id: 0,
        wyrQuestion: ' ... get up early or stay up late',
        wyrAnswer1: 'Early',
        wyrAnswer2: 'Late',
       
        },
        {
          id: 1,
          wyrQuestion: ' ... do school work as a group or by yourself?',
          wyrAnswer1: 'As a group',
          wyrAnswer2: 'By yourself',
         
        },
        {
          id: 2,
          wyrQuestion: ' ... do a book report or a science project for a school assignment?',
          wyrAnswer1: 'Book report',
          wyrAnswer2: 'Science project',
         
        },
      ],
      // user selections message? or messages? or ???
      userSelectionMessages: [], // insted of a string with one message, what could we do?
    }
  }, 
  methods: { // this will show the user choice shoing only one answer for each id
    answerChanged(choice, wyrComponentId){ //
      console.log('This is answer changed', choice, wyrComponentId)
      this.userSelectionMessages[wyrComponentId] = choice // shows selected answer 
    }
  }
}
</script>

<style>

body {
  background: lightskyblue;;
}

#app {
  font-family: Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 40px;
}

li {
  color: navy;
  list-style: square;
  list-style-position: inside;
  font-size: 1.3em;
  font-family: Arial, Helvetica, sans-serif;

}



</style>
