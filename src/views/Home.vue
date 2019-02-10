<template>
  <div class="home">
    <h3>Home</h3>
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
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'home',
}
</script>
