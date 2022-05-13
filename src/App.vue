<template>
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <!-- <hippo></hippo> -->
  <!-- <alphabet></alphabet> -->
  <!-- <fox></fox> -->
  <origami></origami>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import Hippo from './components/Hippo.vue'
// import Alphabet from './components/Alphabet.vue'
// import Fox from './components/Fox.vue'
import Origami from './components/Origami.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    // Hippo,
    // Alphabet,
    // Fox,
    Origami,
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
