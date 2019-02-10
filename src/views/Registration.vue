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
                v-model="form.username"
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
        username: "",
        password: "",
        cpassword: "",
      }
    };
  },
  methods: {
    onSubmit() {
      if(this.form.password && this.form.username && this.form.email){
        if (this.form.password !== this.form.cpassword) {
          alert("Your password doesn't match!");
        }
        else{
          Axios.post("http://localhost:8888/user/registration",{
            userBean : this.form
          })
          .then( response => {
            console.log(response);
            alert(response.msg);
          })
          .catch( ({ response }) => {
            console.log(response);
          });
        }
      }
      else{
        alert("Please fill the form.");
      }
      
      
    }
  }
};
</script>
<style scoped>

</style>
