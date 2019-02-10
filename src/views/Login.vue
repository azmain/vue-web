<template>
  <div class="login">
    <div class="row my-5">
      <div class="col-md-6 offset-md-3">
        <b-card>
            <h3 class="text-center my-3">Login</h3>
          <b-form>
            <b-form-group
              id="email"
              label-for="email"
              description="We'll never share your email with anyone else."
            >
            <b-form-input id="email" type="email" required placeholder="Enter email"></b-form-input>
            </b-form-group>

            <b-form-group id="password" label-for="password">
              <b-form-input id="password" type="password" required placeholder="Enter Password"></b-form-input>
            </b-form-group>

            <b-form-group class="text-center">
                <b-button type="submit" class="form-control" variant="success">Login</b-button>
            </b-form-group>
          </b-form>
        </b-card>
      </div>
    </div>
  </div>
</template>
