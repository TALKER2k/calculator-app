<template>
  <button @click="handleClick" class="button">
    {{ label }}
  </button>
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      required: true,
    },
  },
  methods: {
    handleClick() {
      this.$emit('click', this.label);
    },
  },
};
</script>

<style>
.button {
  width: 50px;
  height: 50px;
  margin: 5px;
  font-size: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f1f1f1;
  cursor: pointer;
}

.button:hover {
  background-color: #ddd;
}
</style>