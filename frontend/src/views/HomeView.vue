<template>
  <div class="home">
    <p id="welc">Irregular Verbs Project </p>
    <div class="verbs">
      <div class="verb-container"><input class="verb" placeholder="v1" id="v1"></div>
      <div class="verb-container"><input class="verb" placeholder="v2" id="v2"></div>
      <div class="verb-container"><input class="verb" placeholder="v3" id="v3"></div>
    </div>
    <div class="btnc">
      <div><button class="btn check" v-on:click="show_result">Check</button></div>
      <div><button class="btn generate" v-on:click="generate">Generate</button></div>
    </div>
    <!--AboutTheProject/-->
  </div>
</template>

<script>
const json = require('../verbs/all.json');
import AboutTheProject from '../components/AboutTheProject.vue'

export default {
  name: 'HomeView',
  components: { AboutTheProject }, 
  mounted() {
      document.title = 'Irregular Verbs Project'
      this.generate()
      /* setInterval(() => {
        document.getElementById('welc').innerText = document.getElementById('welc').innerText+'🇬🇧'
      }, 4000); */
  },
  methods: {
    get_random_verb(obj) {
      return Object.keys(obj)[Math.floor(Math.random()*Object.keys(obj).length)]
    },
    generate() {
      document.getElementById('v1').value = this.get_random_verb(json)
      document.getElementById('v2').value = null
      document.getElementById('v3').value = null
    },
    show_result() {
      let v2 = document.getElementById('v2').value;
      let v3 = document.getElementById('v3').value;

      let v2_a = json[document.getElementById('v1').value][0][2]
      let v3_a = json[document.getElementById('v1').value][0][3]
      if (v2 != v2_a) {
        document.getElementById('v2').style.animation = "wrong_answer 0.999s"
        setTimeout(() => document.getElementById('v2').style.animation = 'none', 1300) 
      } else {
        document.getElementById('v2').style.animation = "correct_answer 0.999s"
        setTimeout(() => document.getElementById('v2').style.animation = 'none', 1300)        
      }
      if (v3 != v3_a) {
        document.getElementById('v3').style.animation = "wrong_answer 0.999s"
        setTimeout(() => document.getElementById('v3').style.animation = 'none', 1300) 
      } else {
        document.getElementById('v3').style.animation = "correct_answer 0.999s"
        setTimeout(() => document.getElementById('v3').style.animation = 'none', 1300)        
      }
      document.getElementById('v2').value = v2_a
      document.getElementById('v3').value = v3_a
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
  transition: .3s;
}
.verb {
  font-family: 'Merriweather';
  font-weight: 700;
  font-size: 35px; 
  width: 500px;
  height: 100px;
  border: 3px solid rgb(0, 0, 0);
  box-shadow: 0px 4px 0px black;
  border-radius: 16.6px;
  text-align: center;
  outline: none;
  margin: 0px 10px 0px 10px;
}
.btnc {
  display: flex;
  margin-top: 30px;
  margin-left: 70%;
}
.btn {
  border: none;
  background: none;
  font-size: 28px;
  border-radius: 4px;
  padding: 7px 31px 7px 31px;
  font-family: 'PT Mono', monospace;
}
.check {
  background-color: rgb(49, 173, 49);
  color: white;
  box-shadow: 0px 4px 0px rgb(46, 161, 46);
  transition: .1s;
}
.check:hover {
  background-color: rgb(46, 161, 46);
  box-shadow: 0px 4px 0px rgb(46, 161, 46);
}
.generate {
  outline: 1px solid rgb(133, 133, 255);
  margin-left: 15px;
  box-shadow: 0px 4px 0px rgb(133, 133, 255);
  transition: .2s;
}
.generate:hover {
  outline: 1px solid rgb(71, 71, 255);
  box-shadow: 0px 4px 0px rgb(71, 71, 255);
}
#welc {
  font-family: 'Merriweather';
  font-weight: 700;
  font-size: 30px;
  text-align: center;
}
@keyframes wrong_answer {
  0% {
    border: 3px solid rgb(0, 0, 0);
    box-shadow: 0px 4px 0px black;    
  }
  20% {
    border: 3px solid rgb(255, 0, 0);
    box-shadow: 0px 4px 0px rgb(255, 0, 0);    
  }
  100% {
    border: 3px solid rgb(0, 0, 0);
    box-shadow: 0px 4px 0px black;    
  }
}
@keyframes correct_answer {
  0% {
    border: 3px solid rgb(0, 0, 0);
    box-shadow: 0px 4px 0px black;    
  }
  20% {
    border: 3px solid rgb(0, 255, 64);
    box-shadow: 0px 4px 0px rgb(0, 255, 64);    
  }
  100% {
    border: 3px solid rgb(0, 0, 0);
    box-shadow: 0px 4px 0px black;    
  }
}
</style>
