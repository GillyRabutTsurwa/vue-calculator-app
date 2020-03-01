<template>
  <div class="calculator">
    <div class="display">
      <span>{{current || "0"}}</span>
    </div>
    <div v-on:click="clear" class="button">AC</div>
    <div v-on:click="sign" class="button">+/-</div>
    <div v-on:click="percent" class="button">%</div>
    <div v-on:click="divide" class="button operator">÷</div>

    <div v-on:click="appendNumber('7')" class="button">7</div>
    <div v-on:click="appendNumber('8')" class="button">8</div>
    <div v-on:click="appendNumber('9')" class="button">9</div>
    <div v-on:click="multiply" class="button operator">x</div>

    <div v-on:click="appendNumber('4')" class="button">4</div>
    <div v-on:click="appendNumber('5')" class="button">5</div>
    <div v-on:click="appendNumber('6')" class="button">6</div>
    <div v-on:click="substract" class="button operator">-</div>

    <div v-on:click="appendNumber('1')" class="button">1</div>
    <div v-on:click="appendNumber('2')" class="button">2</div>
    <div v-on:click="appendNumber('3')" class="button">3</div>
    <div v-on:click="add" class="button operator">+</div>

    <div v-on:click="appendNumber('0')" class="button span-2">0</div>
    <div v-on:click="dot" class="button">.</div>
    <div v-on:click="equals" class="button">=</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      current: "",
      previous: null,
      operator: null,
      operatorClicked: false
    };
  },
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
    appendNumber(number) {
      if (this.operatorClicked) {
        this.current = "";
        this.operatorClicked = false;
      }
      this.current = `${this.current}${number}`;
      console.log(this.current);
    },
    dot() {
      if (this.current.indexOf(".") === -1) {
        this.appendNumber(".");
      }
    },
    setPrevious() {
      this.previous = this.current;
      this.operatorClicked = true;
      console.log(this.previous);
    },
    divide() {
      this.operator = (a, b) => a / b;
      this.setPrevious();
    },
    multiply() {
      this.operator = (a, b) => a * b;
      this.setPrevious();
    },
    substract() {
      this.operator = (a, b) => a - b;
      this.setPrevious();
    },
    add() {
      this.operator = (a, b) => a + b;
      this.setPrevious();
    },
    equals() {
      this.current = `${this.operator(
        parseFloat(this.current),
        parseFloat(this.previous)
      )}`;
      this.previous = null;
    }
  }
};
</script>

<style scoped>
.calculator {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

  width: 30rem;
  margin: 0 auto;
  font-size: 3rem;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: minmax(50px, auto);

  border-radius: 4px;
  overflow: hidden;
  box-shadow: 5px 5px 10px 0px rgba(0, 0, 0, 0.75);
}

.display {
  grid-column: 1 / -1;
  background-color: rgb(49, 84, 145);
  color: #fff;
  font-weight: 100;
  height: 8rem;
}

.display span {
  font-size: 6rem;
  float: right;
  margin-bottom: 2rem;
  margin-right: 3rem;
}

.span-2 {
  grid-column: 1 / span 2;
}

.button {
  background-color: #eee;
  border: 1px solid #999;
  cursor: pointer;
  padding: 1rem;
  text-align: center;
}

.operator {
  background-color: rgb(244, 152, 51);
  color: #fff;
}
</style>
