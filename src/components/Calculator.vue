<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <h1 class="mx-auto heading">Calculator</h1>
      </div>
    </div>
    <hr />
    <div class="row">
      <div class="col">
        <div class="calculator mx-auto ">
          <input class="calculator-screen" v-model="currentValue" disabled />

          <div class="calculator-keys">
            <button type="button" class="operator" @click="plus">+</button>
            <button type="button" class="operator" @click="minus">-</button>
            <button type="button" class="operator" @click="multiply">
              &times;
            </button>
            <button type="button" class="operator" @click="divide">
              &divide;
            </button>

            <button type="button" @click="addNumbers(7)">7</button>
            <button type="button" @click="addNumbers(8)">8</button>
            <button type="button" @click="addNumbers(9)">9</button>

            <button type="button" @click="addNumbers(4)">4</button>
            <button type="button" @click="addNumbers(5)">5</button>
            <button type="button" @click="addNumbers(6)">6</button>

            <button type="button" @click="addNumbers(1)">1</button>
            <button type="button" @click="addNumbers(2)">2</button>
            <button type="button" @click="addNumbers(3)">3</button>

            <button type="button" @click="addNumbers(0)">0</button>
            <button type="button" class="decimal" @click="addDot">.</button>
            <button type="button" class="all-clear" @click="clearDisplay">
              AC
            </button>

            <button type="button" class="equal-sign" @click="equals">=</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data: function() {
    return {
      currentValue: "0",
      operatorSelected: "",
      secondValue: "",
    };
  },
  methods: {
    addNumbers(value) {
      this.currentValue = ''
      this.currentValue = this.currentValue + value;
      if (this.currentValue.length > 7) {
        this.currentValue = this.currentValue.substring(0, 7);
      }
    },
    addDot() {
      if (this.currentValue.includes(".") == false) {
        this.currentValue = this.currentValue + ".";
      }
    },
    clearDisplay() {
      this.currentValue = "0";
    },
    plus() {
      this.operatorSelected = "add";
      this.secondValue = this.currentValue;
      this.currentValue = "";
    },
    minus() {
      this.operatorSelected = "sub";
      this.secondValue = this.currentValue;
      this.currentValue = "";
    },
    multiply() {
      this.operatorSelected = "mul";
      this.secondValue = this.currentValue;
      this.currentValue = "";
    },
    divide() {
      this.operatorSelected = "div";
      this.secondValue = this.currentValue;
      this.currentValue = "";
    },
    equals() {
      if (this.operatorSelected == "add") {
        this.currentValue =
          parseInt(this.secondValue) + parseInt(this.currentValue);
        this.secondValue = "";
      } else if (this.operatorSelected == "sub") {
        this.currentValue =
          parseInt(this.secondValue) - parseInt(this.currentValue);
        this.secondValue = "";
      } else if (this.operatorSelected == "mul") {
        this.currentValue =
          parseInt(this.secondValue) * parseInt(this.currentValue);
        this.secondValue = "";
      } else if (this.operatorSelected == "div") {
        this.currentValue =
          parseInt(this.secondValue) / parseInt(this.currentValue);
        this.secondValue = "";
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.heading{
  color: #fff;
  margin-top: 60px;
  text-align: center;
  font-family: Garamond;
  font-size: 70px;
}
.calculator {
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-top: 50px;
  width: 400px;
  background-color: #6b5e5e;
  border-radius: 20px;
}

.calculator-screen {
  width: 100%;
  font-size: 50px;
  height: 80px;
  border: none;
    border-radius: 20px 20px 0px 0px;

  background-color: #252525;
  color:#fff;
  text-align: right;
  padding-right: 20px;
  padding-left: 10px;
}

button {
  height: 60px;
  background-color: #fff;
  border-radius: 3px;
  border: 1px solid #c4c4c4;
  /* background-color: transparent; */
  font-size: 2rem;
  color: #333;
}

button:hover {
  background-color: #eaeaea;
}

.operator {
  color: #337cac;
}

.all-clear {
  background-color: #f0595f;
  border-color: #b0353a;
  color: #fff;
}

.all-clear:hover {
  background-color: #f17377;
}

.equal-sign {
  background-color: #2e86c0;
  border-color: #337cac;
  color: #fff;
  height: 100%;
  grid-area: 2 / 4 / 6 / 5;
}

.equal-sign:hover {
  background-color: #4e9ed4;
}

.calculator-keys {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-gap: 20px;
  padding: 20px;
}
</style>
