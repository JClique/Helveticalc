<template>
  <div class="calculator">
    <div class="display">0.32118</div>
    <div class="btn">C</div>
    <div class="btn">+/-</div>
    <div class="btn">%</div>
    <div class="btn operator">÷</div>
    <div class="btn">7</div>
    <div class="btn">8</div>
    <div class="btn">9</div>
    <div class="btn operator" style="font-size: 90%;">x</div>
    <div class="btn">4</div>
    <div class="btn">5</div>
    <div class="btn">6</div>
    <div class="btn operator">+</div>
    <div class="btn">1</div>
    <div class="btn">2</div>
    <div class="btn">3</div>
    <div class="btn operator">-</div>
    <div class="btn zero">0</div>
    <div class="btn">.</div>
    <div class="btn operator">=</div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
  }
}
</script>

<style scoped>
.calculator {
  font-size: 5em;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);

  max-width: 600px;
  margin: auto;
  font-weight: bold;

  -moz-user-select:none;
  -webkit-user-select:none;
  -webkit-touch-callout:none;
  -ms-user-select:none;
  user-select:none;
}

.display {
  grid-column: 1 / 5;
  background-color: #333;
  color: white;
  border: 2px solid white;
  text-align: right;
  padding-right: .25em;
}

.zero {
  grid-column: 1 / 3;
}

.btn {
  background-color: #ddd;
  color: #333;
  border: 2px solid white;

  cursor: pointer;
  -moz-user-select:none;
  -webkit-user-select:none;
  -webkit-touch-callout:none;
  -ms-user-select:none;
  -khtml-user-select: none;
  user-select:none;

}

.btn:hover {
  -moz-box-shadow: inset 0 0 50px rgba(0,0,0, 0.1);
  -webkit-box-shadow: inset 0 0 50px rgba(0,0,0, 0.1);
  box-shadow: inset 0 0 50px rgba(0,0,0, 0.1);
}

.btn:active {
  margin: 3px -1px -3px 1px;

  height: -moz-calc(100% - 7px);
  height: -webkit-calc(100% - 7px);
  height: -o-calc(100% - 7px);
  height: calc(100% - 7px);

  width: -moz-calc(100% - 5px);
  width: -webkit-calc(100% - 5px);
  width: -o-calc(100% - 5px);
  width: calc(100% - 5px);

  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.operator {
  background-color: orange;
  color: white;
}

</style>
