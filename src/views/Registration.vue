<template>
  <div class="registration">
    <div class="row my-5">
      <div class="col-md-6 offset-md-3">
        <b-card>
          <h3 class="text-center my-3 pb-2">Register Yourself</h3>
          <b-form>
            <b-form-group
              id="email"
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
            <b-form-group id="username" label-for="name">
              <b-form-input
                id="name"
                type="text"
                v-model="form.name"
                required
                placeholder="Enter name"
                autocomplete="false"
              ></b-form-input>
            </b-form-group>
            <b-form-group id="password" label-for="password">
              <b-form-input
                id="password"
                type="password"
                v-model="form.password"
                required
                placeholder="Enter password"
              ></b-form-input>
            </b-form-group>
            <b-form-group id="cpassword" label-for="cpassword">
              <b-form-input
                id="cpassword"
                type="password"
                v-model="form.cpassword"
                required
                placeholder="Confirm password"
              ></b-form-input>
            </b-form-group>
            <div class="text-center">
              <b-button 
                variant="success" 
                class="form-control"
                @click="onSubmit()"
              >
                SIGN UP
              </b-button>
            </div>
          </b-form>
        </b-card>
      </div>
    </div>
  </div>
</template>

<script>
import Axios from 'axios'
export default {
  name: "Registration",
  data() {
    return {
      form: {
        email: "",
        name: "",
        password: "",
        cpassword: "",
      }
    };
  },
  methods: {
    onSubmit() {
      console.log(event);
      console.log(JSON.stringify(this.form));
      Axios.post("http://192.168.43.92:8888/user/registration",this.form)
      .then( response => {
        console.log(response);
      })
      .catch( error => {
        console.log(error);
      });
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

</style>
