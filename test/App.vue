<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <home></home>
    <!--
    <contacto></contacto>

    <p>Variable {{texto}}t~</p>
    <input v-model="texto" type="string"/>

    <test :message="texto"></test>
    <HelloWorld msg="HELLOOOOOOOOOO"/>

    -->
    <preg7></preg7>
  </div>
</template>
<script>
//import HelloWorld from './components/HelloWorld.vue'
//import test from './components/test.vue'
//import contacto from './components/contacto'
import home from './components/home'
import preg7 from './components/preg7'
//new Vue({
//  el: '#app',
//  data: {
//    texto:''
//  }
//})

export default {
  name: 'App',
  components: {
    //HelloWorld asd
    //test,
    home,preg7
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
