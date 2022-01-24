<script>
import NumberField from './NumberField.vue'

export default {
  data() {
    return {
      numberField1: 0,
      numberField2: 0,
      numberField3: 0,
    }
  },
  computed: {
    sum() {
      return Number(this.numberField1) + Number(this.numberField2) + Number(this.numberField3)
    }
  },
  components: {
    NumberField
  },
  methods: {
    alertSum () {
      if(this.sum>0)
       alert(this.sum)
    }
  }
}
</script>

<template>
  <NumberField v-model="numberField1" :step="1" /><br>
  <NumberField v-model="numberField2" :step="numberField1"/><br>
  <NumberField v-model="numberField3" :step="numberField2" /><br>
  <button class="btn" @click="alertSum()">
    alert sum
  </button>
  {{ sum }}
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
  padding: 20px;
}
.btn {
  margin-top: 15px;
  align-self: flex-end;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
}
</style>