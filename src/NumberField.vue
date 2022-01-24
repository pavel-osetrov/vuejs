<script>
export default {
  props: {
    step: {
      type: Number,
      default: 1,
      required: true,
      validator: function (value) {
        return Math.abs(Number(value));
      }
    },
    modelValue: {
      default: 1,
    },
  },
  emits: ["update:modelValue"],
  data() {
    return {
      value: this.modelValue,
    }
  },
  methods: {
    decreaseValue() {
      if(this.value > 0)
        this.value -= this.step;
        this.$emit("update:modelValue", Number(this.value));
    },
    increaseValue() {
      this.value += this.step;
      this.$emit("update:modelValue", Number(this.value));
    },
    setValue(newValue) {
      this.value = newValue.replace(/\D+/gm, "");
      this.$emit("update:modelValue", Number(this.value));
    }
  }
}
</script>

<template>
  <button class="btn" @click="decreaseValue">-</button>
  <input
      class="input"
      type="number"
      :value="value"
      @input="setValue($event.target.value)"
  >
  <button class="btn" @click="increaseValue">+</button>
</template>

<style scoped>
.input {
  width: 10%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}

</style>