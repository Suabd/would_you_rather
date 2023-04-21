<template>
  <div class="wyr">
   
    <h2>  Would You Rather ..... </h2>

    <h3> {{ question }}</h3>

    <input type="radio" v-model="choice" v-bind:value="answer1" v-on:change="choiceMade">
    <label>{{ answer1 }}</label>
    <input type="radio" v-model="choice" v-bind:value="answer2" v-on:change="choiceMade">
    <label>{{ answer2 }}</label>

  </div>
</template> 

<script>
export default {
  name: 'WouldYouRather',
  props: {
    id: Number,
    question: String,
    answer1: String,
    answer2: String,
  },
  data(){
    return{
      choice:''
    }
  },
  methods: { 
    choiceMade(){ // will should what ever user chice from radio
      // emit an called 'answer-changed' 
      //and  include the value of the data choice
      //and this component's  id 
      this.$emit('answer-changed', this.choice, this.id)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 30px 0 0;
}

.wyr {
  border: 2px  rgb(3, 0, 14) solid;
  background: rgb(250, 248, 143);
  margin: 5px;
  padding: 10px;
  text-align: left;
}




</style>
