<template>
  <div class="register-records">
    <div class="data-card" v-for="(item, index) in studentData" :key="index">
      <RegisterCard :studentData="item"></RegisterCard>
    </div>
    <div class="no-data" v-if="!studentData.length">No Records Yet !!</div>
  </div>
</template>
<script>
import RegisterCard from "./register-card.vue";
export default {
  name: "register-records",
  components: {
    RegisterCard,
  },
  props: {
    studentData: Array,
  },
};
</script>
<style lang="scss">
.register-records {
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 5vh;
  .data-card {
    width: 40vw;
    margin-top: 2vh;
  }
  .no-data {
    // border: 1px solid black;
    font-size: 30px;
    color: rgb(67, 4, 97);
  }
}
</style>
