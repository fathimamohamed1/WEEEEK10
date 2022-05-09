<template>
  <div class="WYR">

 <h2>Please make your choice!</h2>
<h3>{{question}}</h3>

    <input type="radio" v-model="choice" v-bind:value="Answer1" v-on:change="ChoiceMade">
    <label>{{Answer1}}</label>

    <input type="radio" v-model="choice" v-bind:value="Answer2" v-on:change="ChoiceMade">
    <label>{{Answer2}}</label>

  </div>
</template>

<script>

export default {
  name: 'WouldYouRather',
  props: {
   question:String,
    Answer1:String,
    Answer2:String,
  },
  data(){
    return{
      choice:''
    }
  },
  methods:{
    ChoiceMade(){
      this.$emit('option-changed',this.choice)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
.WYR{
  border: 5px black solid;
 background: linen;
  font-style: italic;
  font-size: large;
  margin:10px;
}
</style>
