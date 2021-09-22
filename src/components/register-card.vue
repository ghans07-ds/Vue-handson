<template>
  <div class="register-card">
    <div class="form-card">
      <p class="user-name">Name:{{ studentData.fullName }}</p>
      <p class="user-email">Email:{{ studentData.email }}</p>
      <p class="user-no">MobileNo:{{ studentData.mobileNo }}</p>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    studentData: Object,
  },
};
</script>
<style lang="scss">
.register-card {
  width: 100%;
  background-color: rgb(55, 3, 80);
  box-shadow: 0 0 15px 0px rgba(55, 3, 80, 0.4);

  border-radius: 5px;
  .form-card {
    color: white;
    font-size: 20px;
    padding: 5px;
  }
}
</style>
