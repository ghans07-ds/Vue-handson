<template>
  <div class="register-form">
    <div class="form-container">
      <p
        v-if="!isSuccess && isActive"
        v-bind:style="{ backgroundColor: 'rgb(236, 60, 60)' }"
      >
        Fields should not be empty!
      </p>
      <p
        v-if="isSuccess && isActive"
        v-bind:style="{ backgroundColor: 'green' }"
      >
        Succesfully Registerd!!
      </p>
      <form v-on:submit="registerStudent">
        <div class="input-fields">
          <div class="input-field">
            <input
              type="text"
              v-model="firstName"
              placeholder="Enter First Name"
              autofocus
            />
          </div>
          <div class="input-field">
            <input
              type="text"
              v-model="lastName"
              placeholder="Enter Last Name"
            />
          </div>
          <div class="input-field">
            <input type="email" v-model="email" placeholder="Enter Email" />
          </div>
          <div class="input-field">
            <input
              type="tel"
              v-model="mobileNo"
              placeholder="Enter Mobile No"
            />
          </div>
          <div class="btn-field">
            <input type="submit" name="submit" value="Submit" />
          </div>
        </div>
      </form>
    </div>
  </div>
</template>
<script>
export default {
  name: "register-form",
  data() {
    return {
      firstName: "",
      email: "",
      mobileNo: "",
      lastName: "",
      studentData: [],
      isSuccess: true,
      isActive: false,
    };
  },
  props: {
    isFormSelected: Boolean,
  },
  methods: {
    registerStudent(e) {
      e.preventDefault();
      this.isActive = true;
      this.isSuccess = true;
      if (!this.firstName || !this.email || !this.mobileNo || !this.lastName) {
        this.isSuccess = false;
      }
      this.isSuccess &&
        this.studentData.push({
          firstName: this.firstName,
          lastName: this.lastName,
          fullName: this.fullName,
          email: this.email,
          mobileNo: this.mobileNo,
        });
      this.isSuccess && this.$emit("studentData", this.studentData);
    },
  },
  computed: {
    fullName() {
      return `${this.lastName} ${this.firstName}`.toUpperCase();
    },
  },
  watch: {
    isFormSelected() {
      this.isActive = false;
      this.firstName = this.email = this.mobileNo = this.lastName = "";
    },
  },
  mounted() {
    console.log(this.isFormSelected);
  },
  // methods: {},
};
</script>
<style lang="scss">
.register-form {
  box-sizing: border-box;
  height: 100%;
  width: 100%;
  p {
    margin: 0 30vw;
    margin-top: 30px;
    text-align: center;
    padding: 5px;
    color: white;
    border-radius: 5px;
    font-size: 20px;
  }
  form {
    margin: 10vh 30vw;
    border: 1px solid black;
    .input-fields {
      box-sizing: border-box;
      width: 100%;
      height: 100%;
      padding: 30px 100px;
      box-shadow: 0 0 15px 0px rgba(55, 3, 80, 0.4);
      border-radius: 5px;
    }
    .input-field,
    .btn-field {
      margin: 15px 0;
      input {
        box-sizing: border-box;
        width: 100%;
        padding: 8px;
        font-size: 18px;
        border: 1px solid rgb(55, 3, 80);
        outline: none;
        border-radius: 3px;
      }
    }
    .btn-field {
      margin: 60px 0;
      input {
        width: 100%;
        padding: 8px;
        font-size: 22px;
        height: 5vh;
        color: white;
        background-color: rgb(67, 4, 97);
        border: none;
        border-radius: 7px;
        cursor: pointer;
        box-shadow: 0 0 15px 0px rgba(55, 3, 80, 0.4);
      }
      input:hover {
        background-color: rgb(95, 7, 136);
      }
      input:active {
        font-size: 18px;
      }
    }
  }
}
</style>
