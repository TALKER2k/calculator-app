<template>
  <div class="button-panel">
    <CalculatorButton
      v-for="buttonLabel in buttons"
      :key="buttonLabel"
      :label="buttonLabel"
      @click="handleButtonClick"
    />
  </div>
</template>

<script>
import CalculatorButton from './CalculatorButton.vue';

export default {
  components: {
    CalculatorButton,
  },
  data() {
    return {
      buttons: [
        '1', '2', '3', '/',
        '4', '5', '6', '*',
        '7', '8', '9', '+',
        '0', '.', '=', '-',
        'C', 'CE'
      ],
    };
  },
  methods: {
    handleButtonClick(label) {
      this.$emit('click', label);
    },
  },
};
</script>

<style>
.button-panel {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-gap: 5px;
  max-width: 220px;
  margin-left: -35px;
}
</style>