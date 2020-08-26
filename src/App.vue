<template>
  <div id="app">
    <h1>Neumorphic Calculator</h1>
<Calculator/>
    <h3><strong><span>&copy;</span>2020</strong>  Sam-kay</h3>
  </div>
</template>


<script>
import Calculator from './components/calculator.vue'

export default {
  name:'app',
  components:{
    Calculator
  }
}
</script>

<style >
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
html{
    background-color: #aebdcc;

}

h1{
  font-family:'Courier New', Courier, monospace;
  font-size:50px;
}

span{
  font-size:25px;
}

</style>