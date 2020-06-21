<template>
  <nav class="navbar navbar-expand-sm justify-content-end light-gr"
    role="navigation" aria-label="main navigation">
    <router-link to="/" class="navbar-brand">Home</router-link>
    <router-link v-if="$auth.isAuthenticated" to="/account" class="navbar-brand">My Account</router-link>
    <div class="btn ml-auto mr-1">
      <!-- Check that the SDK client is not currently loading before accessing is methods -->
      <div v-if="!$auth.loading">
        <!-- show login when not authenticated -->
        <a class="navbar-brand" v-if="!$auth.isAuthenticated" @click="login" >
          <strong>Sign in</strong></a>
        <!-- show logout when authenticated -->
        <a class="navbar-brand" v-if="$auth.isAuthenticated" @click="logout" >
          <strong>Log out</strong></a>
      </div>
    </div>
  </nav>
</template>


<style lang="scss" scoped>
nav {
  margin-top: 25px;
  margin-bottom: 30px;
  margin-left: 300px;
  margin-right: 300px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #d88d00;
    }
  }
}
</style>

<script>
export default {
  name: "Nav",
  methods: {
    // Log the user in
    login() {
      this.$auth.loginWithRedirect();
    },
    // Log the user out
    logout() {
      this.$auth.logout({
        returnTo: window.location.origin
      });
    }
  }
};
</script>