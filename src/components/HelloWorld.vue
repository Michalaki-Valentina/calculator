<script>
export default {
  data() {
    return {
      darkTheme: false,
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
  },
};
</script>

<template>
  <div class="calculator" :class="theme">
    <label for="darkmode-toggle" @click="toggleTheme"></label>
    <div class="screen"></div>
    <div class="buttons-container">
      <button class="button">7</button>
      <button class="button">8</button>
      <button class="button">9</button>
      <button class="button">+</button>
      <button class="button">4</button>
      <button class="button">5</button>
      <button class="button">6</button>
      <button class="button">-</button>
      <button class="button">1</button>
      <button class="button">2</button>
      <button class="button">3</button>
      <button class="button">x</button>
      <button class="button color-red">C</button>
      <button class="button">0</button>
      <button class="button">=</button>
      <button class="button">/</button>
    </div>
  </div>
</template>

<style scoped>
.calculator {
  width: 320px;
  height: 450px;
  border: 2px solid black;
  margin: 0 auto;
  background-color: #37374d;
}
.screen {
  width: 280px;
  height: 70px;
  border: 2px solid black;
  margin: 30px auto;
  background-color: azure;
}
.buttons-container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 20px;
}
.button {
  width: 50px;
  height: 50px;
  border: 1px solid black;
  background-color: azure;
  font-size: 15px;
}

.color-red {
  background-color: rgba(255, 0, 0, 1);
  color: white;
  font-weight: 900;
  font-size: 18px;
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

input:checked + label {
  background: #242424;
}
input:checked + label:after {
  left: 490px;
  transform: translateX(-100%);
  background: linear-gradient(180deg, #777, #3a3a3a);
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
