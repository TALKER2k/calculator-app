<template>
  <div class="display">
    {{ currentValue }}
  </div>
</template>

<script>
export default {
  props: {
    currentValue: {
      type: String,
      required: true,
    },
  },
};
</script>

<style>
.display {
  width: 220px;
  height: 50px;
  margin: 5px;
  margin-top: 15px;
  padding: 10px;
  font-size: 30px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f1f1f1;
  text-align: right;
}
</style>