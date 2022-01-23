<template>
<div class="background">
  <img id="logo" alt="Vue logo" src="./assets/logo.png">
  <MainComponent />
</div>
</template>

<script>
import MainComponent from './components/MainComponent.vue'

export default {
  name: 'App',
  components: {
    MainComponent
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
#logo{ 
  max-width:90%;
    height:130px;

}
.background{
  background-color:powderblue;
  border-radius: 20px;
}
</style>
