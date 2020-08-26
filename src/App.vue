<template>
  <div id="app">
    <h1>Neumorphic Calculator</h1>

    <Calculator />
    <h3>
      <strong>
        <span>&copy;</span>2020
      </strong> Sam-kay
    </h3>
    <div id="bugs">
      <h3>current bugs:</h3>you've gotta press the C button to reset the calc afer the qual to sign and some other issues but such will def be corrected as I make progress
    </div>
  </div>
</template>


<script>
import Calculator from "./components/calculator.vue";

export default {
  name: "app",
  components: {
    Calculator,
  },
};
</script>

<style >
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
html {
  background-color: #aebdcc;
}

h1 {
  font-family: "Courier New", Courier, monospace;
  font-size: 50px;
}

span {
  font-size: 25px;
}
#bugs {
  max-width: 250px;
}
</style>