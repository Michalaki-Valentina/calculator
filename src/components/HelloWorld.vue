<script setup></script>

<template>
  <div class="calculator">
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
  background-color: rgba(0, 0, 0, 0.5);
}
</style>
