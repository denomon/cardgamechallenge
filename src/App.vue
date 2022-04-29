<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Card Game Challenge"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
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


.card {
  position: relative;
  width: 105px;
  height: 150px;
  border-radius: 5px;
  border: 1px solid #ccc;
  box-shadow: 0px 0px 5px 0px rgba(0,0,0,0.25);
  float: left;
  left: 25%;


}
.card-value-suit {
  display: inline-block;
  position: absolute;
}
.card-value-suit.top {
  top: 5px;
  left: 5px;
}
.card-value-suit.bot {
  transform: rotate(180deg);
  bottom: 5px;
  right: 5px;
}
.card-suit {
  font-size: 50px;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  left: 25%;
}
</style>
