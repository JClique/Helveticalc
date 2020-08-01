<template>
  <div class="calculator">

    <div class="display">{{ current || '0' }}</div>

    <div @click="clear" class="btn">C</div>
    <div @click="sign" class="btn">+/-</div>
    <div @click="percent" class="btn">%</div>
    <div @click="divide" class="btn operator">÷</div>

    <div @click="append('7')" class="btn">7</div>
    <div @click="append('8')" class="btn">8</div>
    <div @click="append('9')" class="btn">9</div>
    <div @click="times" class="btn operator" style="font-size: 90%;">x</div>

    <div @click="append('4')" class="btn">4</div>
    <div @click="append('5')" class="btn">5</div>
    <div @click="append('6')" class="btn">6</div>
    <div @click="add" class="btn operator">+</div>

    <div @click="append('1')" class="btn">1</div>
    <div @click="append('2')" class="btn">2</div>
    <div @click="append('3')" class="btn">3</div>
    <div @click="minus" class="btn operator">-</div>

    <div @click="append('0')" class="btn zero">0</div>
    <div @click="dot()" class="btn">.</div>
    <div @click="equal" class="btn operator">=</div>

  </div>
</template>

<script>
export default {
  name: 'Calc',
  data() {
    return {
      current: '',
      previous: null,
      operator: null,
      operatorClicked: false,
    }
  },
  methods: {
    clear() {
      this.current = '';
    },
    sign() {
      this.current = this.current.charAt(0) === '-' ?    // if current starts with '-'
        this.current.slice(1) : `-${this.current}`;      // remove first char or return current with '-' prefixed
    },
    percent() {
      this.current = `${parseFloat(this.current) / 100}`
    },
    append(number) {
      if (this.operatorClicked) {
        this.current = '';
        this.operatorClicked = false;
      }
      if (this.current.length < 10) {    // limits input to 10 chars
        this.current = `${this.current}${number}`;
      }
    },
    dot() {
      if (this.current.indexOf('.') === -1) {     // if '.' is not already within current
        this.append('.');
      }
    },
    setPrevious() {
      this.previous = this.current;
      this.operatorClicked = true;
    },
    setActive(target) {
      let elems = document.querySelectorAll(".active");    // returns all '.active' elements
      [].forEach.call(elems, function(el) {                // for each el in elems
        el.classList.remove("active");                     // remove '.active'
      });
      if (target) {                       // if target is given
        target.classList.add('active')    // add '.active' to target
      }
    },
    add(e) {
      this.operator = (a, b) => a + b;    // creates operator
      this.setPrevious();                 // sets previous
      this.setActive(e.target);           // sets active operator class
    },
    minus(e) {
      this.operator = (a, b) => a - b;
      this.setPrevious();
      this.setActive(e.target);
    },
    divide(e) {
      this.operator = (a, b) => a / b;
      this.setPrevious();
      this.setActive(e.target);
    },
    times(e) {
      this.operator = (a, b) => a * b;
      this.setPrevious();
      this.setActive(e.target);
    },
    equal() {
      if (this.current && this.previous) {    // prevents NaaN
        let answer = this.operator(           // limits to 10 decimal places for max width of calc
          parseFloat(this.current),
          parseFloat(this.previous)
        )
        this.current = `${Number((answer).toFixed(10))}`;
        this.previous = null;
      }
      this.setActive();
    }
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
  direction: rtl;
  padding: 0 .25em;
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

.btn.active {
  background-color: #ff8a00;
}

.operator {
  background-color: orange;
  color: white;
}

</style>
