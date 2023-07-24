<template>
  <div class="calculator">
    <CalculatorDisplay :currentValue="currentValue" />
    <ButtonPanel @click="handleButtonClick" />
  </div>
</template>

<script>
import CalculatorDisplay from './CalculatorDisplay.vue';
import ButtonPanel from './ButtonPanel.vue';

export default {
  components: {
      CalculatorDisplay,
    ButtonPanel,
  },
  data() {
    return {
      currentValue: '',
      calcVal: '',
      operators: null,
      prevCalcVal: ''
    };
  },
  methods: {
handleButtonClick(label) {
  if (!isNaN(label) || label === '.') {
    this.currentValue += label;
  } else if (label === 'CE') {
    this.currentValue = this.currentValue.slice(0, -1);
  }
    else if (label === 'C') {
    this.currentValue = '';
  }  else if (['/', '+', '-', '*'].includes(label)) {
    this.operators = label;
    this.prevCalcVal = parseFloat(this.currentValue).toString();
    this.currentValue = '';
  } else if (label === '=') {
    try {
      this.currentValue = eval(
        parseFloat(this.prevCalcVal) + this.operators + parseFloat(this.currentValue)
      ).toString();
      this.prevCalcVal = '';
      this.operators = null;
    } catch (error) {
      this.currentValue = 'Error';
    }
  }
},
},

};
</script>

<style>
.calculator {
  border: 1px solid #ccc;
  border-radius: 5px;
  width: 300px;
  height: 430px;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 20px;
}
</style>