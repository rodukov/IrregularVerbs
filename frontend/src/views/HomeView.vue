<template>
  <div class="home">
    <div class="description-container" id="description-container">
      <p class="description"></p>
    </div>
    <p id="welc">Irregular Verbs Project</p>
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
    <!--why_we/-->
  </div>
</template>

<script>
const json = require('../verbs/all.json');
import AboutTheProject from '../components/AboutTheProject.vue'
import why_we from '../components/why_we.vue'

export default {
  name: 'HomeView',
  components: { AboutTheProject, why_we }, 
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
      document.getElementsByClassName("description-container")[0].style.display = "inline-block";
      document.getElementsByClassName('description')[0].innerText = json[document.getElementById('v1').value][0]["description"]
      document.getElementsByClassName("description-container")[0].style.transform = "translateX(0px)";
      document.getElementsByClassName("description-container")[0].style.opacity = "1";
      setTimeout(() => {
        document.getElementsByClassName("description-container")[0].style.transform = "translateX(150%)"
        document.getElementsByClassName("description-container")[0].style.opacity = "0";
        document.getElementsByClassName("description-container")[0].style.display = "none";
      }, 4300)
      document.getElementById('v2').value = v2_a
      document.getElementById('v3').value = v3_a
    }
  }
}
</script>

<style>
.description-container {
  position: absolute;
  background: rgba(230, 230, 230, 0.205);
  backdrop-filter: blur(9.5px);
  border-radius: 7px 0px 0px 7px;
  top: 50px;
  left: 0;
  right: 0;
  width: 30%;
  padding: 5px;
  margin-left: auto;
  text-align: center;
  border-left: 3px solid black;
  border-top: 3px solid black;
  border-bottom: 3px solid black;
  transform: translateX(150%);
  box-shadow: 0px 5px 10px rgba(184, 184, 184, 0.473);
  transition: .3s;
  opacity: 0;
  display: none;
}

.description {
  font-family: 'Merriweather';
  font-size: 25px;
}
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

@media (max-width: 1608px) {
  .verbs {
    display: block;
    margin-left: auto;
    margin-right: auto;
    width: 510px;
  }
  .verb {
    margin-top: 10px;
    margin-left: 0px;
  }
  .btnc {
    display: flex;
    margin-left: auto;
    margin-right: auto;
    width: 357px;
  }
}
@media (max-width: 530px) {
  .verb {
    width: 97%;
  }
  .verbs {
    width: 97%;
  }
}
@media (max-width: 370px) {
  .btn {
    font-size: 16px;
  }
  .btnc {
    width: 263.8px;
    margin-top: 10px;
  }
}
</style>
