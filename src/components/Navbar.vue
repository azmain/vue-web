<template>
  <b-navbar toggleable="md" type="dark" variant="info">
    <div class="container">
      <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>

      <b-navbar-brand href="#">
          <img src="../assets/logo.png" alt="Logo" width="30px" height="30px">
      </b-navbar-brand>

      <b-navbar-nav class="ml-auto" v-if="!authUser">
          <router-link class="nav-link" to="/login">
            Login
          </router-link>
          <router-link class="nav-link" to="/signup">
            SignUp
          </router-link>
      </b-navbar-nav>

      <b-collapse is-nav id="nav_collapse" v-if="authUser">
        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto" >
          <b-nav-item-dropdown right >
            <!-- Using button-content slot -->
            <template slot="button-content">
              <em>Hey, {{ authUser }}</em>
            </template>
            <b-dropdown-item href="#">Profile</b-dropdown-item>
            <b-dropdown-item href="#">Signout</b-dropdown-item>
          </b-nav-item-dropdown>
        </b-navbar-nav>
      </b-collapse>
    </div>
  </b-navbar>
</template>

<script>
export default {
  mounted() {

  },
  computed: {
    authUser(){
      return this.$root.auth.username;
    }
  }
}
</script>

