<template>
  <div class="registration">
    <div class="row my-5">
      <div class="col-md-6 offset-md-3">
        <b-card>
          <h3 class="text-center my-3 pb-2">Register Yourself</h3>
          <b-form>
            <!-- Name -->
            <b-form-group id="username" label-for="name">
              <b-form-input
                id="name"
                v-bind:class="{'is-invalid' : errors.username, 'is-valid' : !errors.username && isSubmitted}"
                type="text"
                v-model="form.username"
                required
                placeholder="Enter name"
                autocomplete="false"
              ></b-form-input>
              <div class="errors" v-if="errors.username">
                <small class="text-danger" v-for="error in errors.username" :key="error">
                  {{ error }}
                </small>
              </div>
            </b-form-group>
            <!-- Email -->
            <b-form-group
              id="email"
              label-for="email"
              description="We'll never share your email with anyone else."
            >
              <b-form-input
                id="email"
                v-bind:class="{'is-invalid' : errors.email, 'is-valid' : !errors.email && isSubmitted}"
                type="email"
                v-model="form.email"
                required
                placeholder="Enter email"
                autocomplete="false"
              ></b-form-input>
              <div class="errors" v-if="errors.email">
                <small class="text-danger" v-for="error in errors.email" :key="error">
                  {{ error }}
                </small>
              </div>
            </b-form-group>
            <!-- Password -->
            <b-form-group 
              id="password" 
              label-for="password">
              <b-form-input
                id="password"
                v-bind:class="{'is-invalid' : errors.password, 'is-valid' : !errors.password && isSubmitted}"
                type="password"
                v-model="form.password"
                required
                placeholder="Enter password"
              ></b-form-input>
              <div class="errors" v-if="errors.password">
                <small class="text-danger" v-for="error in errors.password" :key="error">
                  {{ error }}
                </small>
              </div>
            </b-form-group>
            <!-- Confirm Password -->
            <b-form-group id="cpassword" label-for="cpassword">
              <b-form-input
                id="cpassword"
                v-bind:class="{'is-invalid' : errors.cpassword, 'is-valid' : !errors.cpassword && isSubmitted}"
                type="password"
                v-model="form.cpassword"
                required
                placeholder="Confirm password"
              ></b-form-input>
              <div class="errors" v-if="errors.cpassword">
                <small class="text-danger" v-for="error in errors.cpassword" :key="error">
                  {{ error }}
                </small>
              </div>
            </b-form-group>
            <div class="text-center">
              <b-button 
                :disabled="loading"
                variant="success" 
                class="form-control"
                @click="onSubmit()"
              >
                <i class="fa fa-spin fa-spinner" v-if="true"></i>
                {{ loading? "" : "SignUp" }}
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
      },
      errors: {

      },
      isSubmitted: false,
      loading: false
    };
  },
  methods: {
    onSubmit() {
      this.isSubmitted = true;
      this.loading = true;
      var validationCheck = this.validation(this.form);
      if(validationCheck){
        Axios.post("http://localhost:8888/user/registration",{
            userBean : this.form
          })
          .then( ({ data }) => {
            console.log(data);
            localStorage.setItem("auth",JSON.stringify(data.data));
            this.$root.auth = data.data;
            alert(data.msg);
            this.loading = false;
            this.$router.push("/");
          })
          .catch( ({ response }) => {
            console.log(response);
            this.loading = false;
          });
      }
      this.loading = false;
    },
    validation(data){
      let temp = {};
      this.errors = {};
      if(!data.username){
        temp.username = ["Name field is required."];
      }
      if(!data.email){
        temp.email = ["Email field is required."];
      }
      if(!data.password){
        temp.password = ["Password field is required."];
      }
      if(!data.cpassword){
        temp.cpassword = ["Confirm your password."];
      }
      if(data.password != data.cpassword){
        temp.cpassword = ["Your password does not match."]; 
      }

      this.errors = temp;
      if(Object.keys(this.errors).length == 0){
        return true;
      }
      return false;
    }
  }
};
</script>
<style scoped>

</style>
