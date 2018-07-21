<template>
  <div id="app">
    <img src="./assets/logo.png">
    <!-- simple direcitve -->
    <!-- <h1 v-highlight>{{ msg }}</h1> -->

    <!-- directive with value -->
    <!-- <h1 v-highlight="'blue'" >{{ msg }}</h1> -->

    <!-- directive with binding arg -->
    <h1 v-highlight:background="'blue'" >{{ msg |upper}}</h1>
    <h1 v-highlight="'blue'" >{{ msg }}</h1>

    <button v-customOn="clicked" >Click Me</button>

    <input v-model="str" v-creditCard="jinal" >
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      str:'',
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods:{
    clicked(){
      alert("clicked");
    },
    jinal(){
      let trimmed = this.str.replace(/\s+/g, '');
if (trimmed.length > 16) {
        trimmed = trimmed.substr(0, 16);
    }

let numbers = [];
for (let i = 0; i < trimmed.length; i += 4) {
        numbers.push(trimmed.substr(i, 4));
    }
    this.str = numbers.join(' ');
    }
  },
  filters:{
    upper(value){
      return value.toUpperCase();
    }
  },
  directives:{
    customOn:{
      bind(el,binding){
          el.onclick=function(){
            binding.value();
          }
      }
    },
    creditCard:{
      bind(el,binding){
        el.onkeyup=function(){
          binding.value();
        }
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
