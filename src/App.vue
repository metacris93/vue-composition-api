<template>
  <input type="date" v-model="birthday">
  <ScriptSetup user="Cristian" email="cristian.pisco@outlook.com" />
  <!-- <UserRepositories user="Cristian" email="cristian.pisco@outlook.com" /> -->
</template>

<script>
// import UserRepositories from './components/UserRepositories'
import ScriptSetup from './components/ScriptSetup'
import {provide, ref} from 'vue'

export default {
  name: 'App',
  components: {
    ScriptSetup
    // UserRepositories
  },
  setup() {
    const birthday = ref('')
    provide("birthday", birthday)
    return {
      birthday
    }
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
