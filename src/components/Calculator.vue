<script>
export default {
  data() {
    return {
      current: "",
      operator: null,
      previous: null,
      operatorClicked: false,
    };
  },
  computed: {},
  methods: {
    clear() {
      this.current = "";
    },
    sign() {
      this.current =
        this.current.charAt(0) === "-"
          ? this.current.slice(1)
          : `-${this.current}`;
    },
    percent() {
      this.current = `${parseFloat(this.current) / 100}`;
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
        this.append(".");
      }
    },
    setPrevious() {
      this.previous = this.current;
      this.operatorClicked = true;
    },
    divide() {
      this.operator = (a, b) => a / b;
      this.setPrevious();
    },
    minus() {
      this.operator = (a, b) => a - b;
      this.setPrevious();
    },
    add() {
      this.operator = (a, b) => a + b;
      this.setPrevious();
    },
    times() {
      this.operator = (a, b) => a * b;
      this.setPrevious();
    },
    calc() {
      this.current = `${this.operator(
        parseFloat(this.previous),
        parseFloat(this.current)
      )}`;
      this.previous = null;
    },
  },
};
</script>

<template>
  <div class="calculator">
    <div class="display-container">
      <div class="display">{{ current || "0" }}</div>
    </div>
    <div class="btn" @click="clear">C</div>
    <div class="btn" @click="sign">+/-</div>
    <div class="btn" @click="percent">%</div>
    <div class="btn btn-operator" @click="divide">÷</div>
    <div class="btn" @click="append('7')">7</div>
    <div class="btn" @click="append('8')">8</div>
    <div class="btn" @click="append('9')">9</div>
    <div class="btn btn-operator" @click="times">x</div>
    <div class="btn" @click="append('4')">4</div>
    <div class="btn" @click="append('5')">5</div>
    <div class="btn" @click="append('6')">6</div>
    <div class="btn btn-operator" @click="minus">-</div>
    <div class="btn" @click="append('1')">1</div>
    <div class="btn" @click="append('2')">2</div>
    <div class="btn" @click="append('3')">3</div>
    <div class="btn btn-operator" @click="add">+</div>
    <div class="btn btn-zero" @click="append('0')">0</div>
    <div class="btn" @click="dot">.</div>
    <div class="btn btn-operator" @click="calc()">=</div>
  </div>
</template>

<style scoped>
.calculator {
  display: grid;
  margin: 0 auto;
  width: 250px;
  font-size: 25px;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}
.display-container {
  display: grid;
  align-items: center;
  justify-content: end;
  grid-column: 1 / 5;
  grid-row: 1 / 3;
  background-color: #333;
  color: white;
  overflow: hidden;
}

.display {
  margin: 0 15px;
}

.btn {
  border: 1px solid #999;
  background-color: #eee;
  text-align: center;
  align-items: center;
}
.btn-zero {
  grid-column: 1/3;
}
.btn-operator {
  background-color: orange;
  color: white;
}
</style>
