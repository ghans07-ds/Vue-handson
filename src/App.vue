<template>
  <div class="main-app">
    <div class="heading">REGISTRATION FORM</div>
    <div class="navigation-btns">
      <button
        class="show-form"
        type="submit"
        v-on:click="showForm"
        v-bind:class="{ isActive: isActive }"
      >
        Form
      </button>
      <button
        class="show-records"
        type="submit"
        v-on:click="showRecords"
        v-bind:class="{ isActive: !isActive }"
      >
        Records
      </button>
    </div>
    <div class="main-content">
      <keep-alive>
        <component
          v-bind:is="component"
          v-bind:studentData="studentData"
          v-bind:isFormSelected="isFormSelect"
          v-on:studentData="getstudentData($event)"
        ></component>
      </keep-alive>
    </div>
  </div>
</template>
<script>
import RegisterForm from "./components/register-form.vue";
import RegisterRecords from "./components/register-records.vue";
export default {
  components: {
    "register-form": RegisterForm,
    "register-records": RegisterRecords,
  },

  data() {
    return {
      component: "register-form",
      studentData: [],
      isActive: true,
      isFormSelect: true,
    };
  },
  methods: {
    getstudentData(data) {
      this.studentData = data;
    },
    showForm() {
      this.component = "register-form";
      this.isActive = true;
      this.isFormSelect = !this.isFormSelect;
    },
    showRecords() {
      this.component = "register-records";
      this.isActive = false;
    },
  },
};
</script>
<style lang="scss">
.main-app {
  .heading {
    height: 10vh;
    width: 100vw;
    background-color: rgb(67, 4, 97);
    color: rgb(255, 255, 255);
    text-align: center;
    line-height: 10vh;
    font-size: 35px;
  }
  .navigation-btns {
    width: 100vw;
    height: 5vh;

    button {
      box-sizing: border-box;
      height: 5vh;
      width: 50%;
      border: none;
      font-size: 22px;
      cursor: pointer;
    }
    .isActive {
      background-color: rgb(67, 4, 97);
      color: white;
    }
    .show-records {
      border-left: 1px solid rgb(130, 19, 233);
    }
  }
  .main-content {
    width: 100vw;
    height: 85vh;
  }
}
</style>
