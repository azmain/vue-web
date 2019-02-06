<template>
  <div class="registration">
    <b-container>
      <b-row align-h="center" class="registration-form">
        <b-col align-self="center" cols="6">
          <div class="text-center">
            <h3>Register Yourself</h3>
          </div>
          <b-form @submit="onSubmit" @reset="onReset" v-if="show">
            <b-form-group
              id="email"
              label="Email address:"
              label-for="email"
              description="We'll never share your email with anyone else."
            >
              <b-form-input
                id="email"
                type="email"
                v-model="form.email"
                required
                placeholder="Enter email"
                autocomplete="false"
              ></b-form-input>
            </b-form-group>
            <b-form-group id="username" label="Your Name:" label-for="name">
              <b-form-input
                id="name"
                type="text"
                v-model="form.name"
                required
                placeholder="Enter name"
                autocomplete="false"
              ></b-form-input>
            </b-form-group>
            <b-form-group id="password" label="Your Password:" label-for="password">
              <b-form-input
                id="password"
                type="password"
                v-model="form.password"
                required
                placeholder="Enter password"
              ></b-form-input>
            </b-form-group>
            <b-form-group id="cpassword" label="Confirm Password:" label-for="cpassword">
              <b-form-input
                id="cpassword"
                type="password"
                v-model="form.cpassword"
                required
                placeholder="Confirm password"
              ></b-form-input>
            </b-form-group>
            <div class="text-center">
              <b-button :size="size" :variant="signup" style="margin-bottom:5px;">
                SIGN UP
              </b-button>
            </div>
          </b-form>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  name: "Registration",
  data() {
    return {
      form: {
        email: "",
        name: "",
        password: "",
        cpassword: "",
      },
      show: true,
        size: "sm",
        signup: "success",
    };
  },
  methods: {
    onSubmit(evt) {
      evt.preventDefault();
      alert(JSON.stringify(this.form));
    },
    onReset(evt) {
      evt.preventDefault();
      /* Reset our form values */
      this.form.email = "";
      this.form.name = "";
      this.form.food = null;
      this.form.checked = [];
      /* Trick to reset/clear native browser form validation state */
      this.show = false;
      this.$nextTick(() => {
        this.show = true;
      });
    }
  }
};
</script>
<style scoped>
.registration {
  background-color: #171c23;
  height: 100vh;
}
.registration-form {
  background-color: #859ec1;
  border-radius: 3px;
}
</style>
