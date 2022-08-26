<template>
  <div class="home">
    <p id="test"></p>
    <div class="verbs">
      <div class="verb-container"><input class="verb" placeholder="v1" id="v1"></div>
      <div class="verb-container"><input class="verb" placeholder="v2" id="v2"></div>
      <div class="verb-container"><input class="verb" placeholder="v3" id="v3"></div>
    </div>
    <div><button class="check" v-on:click="show_result">Check</button></div>
  </div>
</template>

<script>
const json = require('../verbs/all.json'); 
export default {
  name: 'HomeView',
  mounted() {
      document.title = 'Irregular Verbs Project'
      document.getElementById('v1').value = this.get_random_verb(json)
  },
  methods: {
    get_random_verb(obj) {
      return Object.keys(obj)[Math.floor(Math.random()*Object.keys(obj).length)]
    },
    show_result() {

      document.getElementById('v2').value = json[document.getElementById('v1').value][0][2]
      document.getElementById('v3').value = json[document.getElementById('v1').value][0][3]
    }
  }
}
</script>

<style>
.verbs {
  display: flex;
  align-items: center;
  justify-content: center;
  padding-top: 10px;
  padding-bottom: 10px;
}
.verb {
  font-family: 'Arial';
  font-size: 35px; 
  width: 500px;
  height: 100px;
  border: 3px solid rgb(0, 0, 0);
  border-radius: 16.6px;
  text-align: center;
  outline: none;
  margin: 0px 10px 0px 10px;
}
</style>
