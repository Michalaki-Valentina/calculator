<script>
import { getTransitionRawChildren } from "vue";

export default {
  data() {
    return {
      darkTheme: false,
      current: "",
      operator: null,
      previous: null,
      operatorClicked: false,
    };
  },
  computed: {
    theme() {
      return this.darkTheme ? "dark-theme" : "light-theme";
    },
  },
  methods: {
    toggleTheme() {
      this.darkTheme = !this.darkTheme;
    },
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
    equal() {
      this.current = `${this.operator(
        parseFloat(this.current),
        parseFloat(this.previous)
      )}`;
    },
  },
};
</script>

<template>
  <div class="calculator" :class="theme">
    <!-- <label for="darkmode-toggle" @click="toggleTheme"></label> -->
    <div class="display">{{ current || "0" }}</div>
    <div class="btn" @click="clear">C</div>
    <div class="btn" @click="sign">+/-</div>
    <div class="btn" @click="percent">%</div>
    <div class="btn operator" @click="devide">÷</div>
    <div class="btn" @click="append('7')">7</div>
    <div class="btn" @click="append('8')">8</div>
    <div class="btn" @click="append('9')">9</div>
    <div class="btn operator" @click="times('x')">x</div>
    <div class="btn" @click="append('4')">4</div>
    <div class="btn" @click="append('5')">5</div>
    <div class="btn" @click="append('6')">6</div>
    <div class="btn operator" @click="minus('-')">-</div>
    <div class="btn" @click="append('1')">1</div>
    <div class="btn" @click="append('2')">2</div>
    <div class="btn" @click="append('3')">3</div>
    <div class="btn operator" @click="add('+')">+</div>
    <div class="btn zero" @click="append('0')">0</div>
    <div class="btn" @click="dot">.</div>
    <div class="btn operator" @click="equal('=')">=</div>
  </div>
</template>

<style scoped>
.calculator {
  margin: 0 auto;
  width: 250px;
  font-size: 25px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}
.display {
  grid-column: 1 / 5;
  grid-row: 1 / 3;
  background-color: #333;
  color: white;
}

.btn {
  border: 1px solid #999;
  background-color: #eee;
  text-align: center;
  align-items: center;
}

.zero {
  grid-column: 1/3;
}
.operator {
  background-color: orange;
  color: white;
}
.button:active {
  background-color: rgba(220, 216, 239, 0.931);
}
.dark-theme {
  background-color: #333333;
  color: #ffffff;
}
.light-theme {
  background-color: #ffffff;
  color: #000000;
}
label {
  width: 50px;
  height: 20px;
  position: relative;
  display: block;
  background: #ebebeb;
  border-radius: 200px;
  box-shadow: inset 0px 5px 15px rgba(0, 0, 0, 0.4),
    inset 0px -5px 15px rgba(255, 255, 255, 0.4);
  cursor: pointer;
  transition: 0.3s;
}
label:after {
  content: "";
  width: 18px;
  height: 18px;
  position: absolute;
  top: 1px;
  left: 1px;
  background: linear-gradient(180deg, #ffcc89, #d8860b);
  border-radius: 18px;
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.2);
  transition: 0.3s;
}
</style>

<!-- <style lang="scss">
.calculator.dark-theme {
  button {
    color: red;
  }

  input {
    color: white;
  }
}

.calculator.light-theme {
  button {
    color: white;
  }

  input {
    color: red;
  }
}
</style> -->
