<template>
  <div class="parent-container">
    {{ msg }}/{{ age }}
    <button @click="toggleDetails">Toggle</button>
    <PageTitle
      v-bind:title="title"
      v-bind:likes="likeCnt"
      v-bind:isOk="OkVal"
      :memberList="members"
      :isShow="showDetail"
      @child-clicked="handleChildClick"
      ref="page-component"
    />
  </div>
</template>

<script>
import PageTitle from "../components/PageTitle.vue";
export default {
  components: {
    PageTitle,
  },
  data() {
    return {
      msg: "Parent Component",
      age: 0,
      title: "Dynamic Data from Parent",
      likeCnt: 3,
      OkVal: true,
      showDetail: true,
      members: [
        { name: "father", age: 40 },
        { name: "mather", age: 35 },
        { name: "son", age: 8 },
      ],
    };
  },
  methods: {
    toggleDetails() {
      this.showDetail = !this.showDetail;
    },
    handleChildClick(payload = { name: "Lee", age: 0 }) {
      this.msg = payload.name;
      this.age = payload.age;
    },
    sum(num1 = 0, num2 = 0) {
      return num1 + num2;
    },
  },
  mounted() {
    //console.log(this);
  },
};
</script>

<style scoped>
.parent-container {
  border: 2px solid green;
}
</style>
