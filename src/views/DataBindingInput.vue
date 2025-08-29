<template>
  <h3><input type="text" v-model="valueText" /></h3>
  <h3><input type="number" v-model.number="valueNum" /></h3>
  <p>
    <select v-on:change="operateFunc" v-model="operator">
      <option value="+">더하기</option>
      <option value="-">빼기</option>
      <option value="*">곱하기</option>
      <option value="/">나누기</option>
    </select>
  </p>

  <h3>
    <button v-on:click="operateFunc">결과</button>
  </h3>
  <p>{{ valueText }}</p>
  <p>{{ operator }}</p>
  <b style="red">{{ result }}</b>
</template>

<script>
export default {
  data() {
    return {
      valueText: "0",
      valueNum: 10,
      sumVal: 0,
      operator: "*",
      result: 0,
    };
  },
  methods: {
    sumNumber() {
      this.sumVal = this.valueText + this.valueNum;
    },
    multiNumber() {
      this.multiVal = this.valueText * this.valueNum;
    },
    minusNumber() {
      this.minusVal = this.valueText - this.valueNum;
    },
    operateFunc() {
      let result = 0;
      if (this.operateFunc == "+") {
        result = this.valueText + this.valueNum;
      }
      this.result = `${this.valueText}${this.operator}${this.valueNum} = ${result}`;
    },
  },
  beforeUpdate() {
    console.log("beforeUpdate");
  },
  updated() {
    console.log("updated");
  },
};
</script>

<style scoped></style>
