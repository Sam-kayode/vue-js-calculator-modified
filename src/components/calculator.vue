<template>
  <div id="calc">
    <div class="calculator">
      <div class="display">{{current || 0}}</div>
      <div class="btn" @click="clear">C</div>
      <div class="btn" @click="sign">+/-</div>
      <div class="btn" @click="percent">%</div>
      <div class="btn operator" @click="divide">/</div>
      <div class="btn" @click="append('7')">7</div>
      <div class="btn" @click="append('8')">8</div>
      <div class="btn" @click="append('9')">9</div>
      <div class="btn operator" @click="times">x</div>
      <div class="btn" @click="append('4')">4</div>
      <div class="btn" @click="append('5')">5</div>
      <div class="btn" @click="append('6')">6</div>
      <div class="btn operator" @click="minus">-</div>
      <div class="btn" @click="append('1')">1</div>
      <div class="btn" @click="append('2')">2</div>
      <div class="btn" @click="append('3')">3</div>
      <div class="btn operator" @click="add">+</div>
      <div class="btn" id="zero" @click="append('0')">0</div>
      <div class="btn" @click="dot">.</div>
      <div class="btn operator" @click="equal">=</div>
    </div>
    
  </div>
</template>

<script>
export default {
  data() {
    return {
      previous: null,
      current: "",
      operator: null,
      operatorClicked: false,
      memory: null,
    };
  },
  methods: {
    clear() {
      this.current = "";
      this.previous= "";
    },
    sign() {
      if (this.current.charAt(0) === "-") {
        this.current = this.current.slice(1);
      } else if (this.current.charAt(0) !== "-" && this.current > 0) {
        this.current = `-${this.current}`;
      }
    },
    percent() {
      this.current = this.current / 100;
    },
    append(number) {
      if (this.operatorClicked) {
        this.current = "";
        this.operatorClicked = false;
      }

      this.current = `${this.current}${number}`;
    },
    dot() {
      if (this.current.indexOf(".") === -1) {
        this.current = `${this.current}.`;
      }
    },
    setPrevious() {
      this.previous = this.current;
      this.operatorClicked = true;
    },
    divide() {
        if (this.current !== "" && this.previous !== "") {
        this.current = `${this.operator(
          parseFloat(this.previous),
          parseFloat(this.current)
        )}`;
      } 
      this.operator = (a, b) => a / b;
      this.setPrevious();
    },
    times() {
       if (this.current !== "" && this.previous !== "") {
        this.current = `${this.operator(
          parseFloat(this.previous),
          parseFloat(this.current)
        )}`;
      } 
      this.operator = (a, b) => a * b;
      this.setPrevious();
    },
    minus() {
       if (this.current !== "" && this.previous !== "") {
        this.current = `${this.operator(
          parseFloat(this.previous),
          parseFloat(this.current)
        )}`;
      } 
      this.operator = (a, b) => a - b;
      this.setPrevious();
    },
    add() {
      if (this.current !== "" && this.previous !== "") {
        this.current = `${this.operator(
          parseFloat(this.previous),
          parseFloat(this.current)
        )}`;
      } 
        this.operator = (a, b) => a + b;
        this.setPrevious();
      
    },
    equal() {
      this.current = `${this.operator(
        parseFloat(this.previous),
        parseFloat(this.current)
      )}`;
      this.previous = null;
    },
  },
};
</script>

<style scoped>
#calc {
  border: 7px solid #1e3546;
  width: fit-content;
  border-radius: 35px;
  background-color: #1e3546;
  margin: auto;
}
.calculator {
  width: 330px;
  display: grid;
  font-size: 40px;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  border-radius: 35px;
  background: linear-gradient(145deg, #20394b, #1b303f);
  box-shadow: 5px 5px 10px #0c151c, -5px -5px 10px #305570;
  padding: 0px 1px 10px 1px;
  border: 10px solid #1e3546;
}
.display {
  grid-column: 1/5;
  color: white;
  text-align: right;
  padding: 5px;
  margin: 5px;
  font-size: 70px;
  border-radius: 27px;
  background: linear-gradient(145deg, #1b303f, #20394b);
  box-shadow: 8px 8px 16px #192c3a, -8px -8px 16px #233e52;
  overflow: hidden;
}

.btn {
  color: white;
  border-radius: 17px;
  background: #1e3546;
  border-radius: 17px;
  background: #1e3546;
  box-shadow: 5px 5px 6px #152530, -5px -5px 6px #27455c;
  margin: 9px;
  padding: 5px;
  border: px solid #1e3546;
  font-size: 40px;
  font-weight: lighter;
}

.btn:hover {
  background: linear-gradient(315deg, #1b303f, #20394b);
  box-shadow: -5px -5px 13px #172835, 5px 5px 13px #254257;
}
#zero {
  grid-column: 1/3 !important;
}

.operator {
  color: orange;
  border: 0px;
}
</style>