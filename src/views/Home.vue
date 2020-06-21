<template>
  <main>
    <h1>The CrazyWebDev Company™</h1>
    <div class="button-block">
  <!--<button v-if="!$auth.isAuthenticated" @click="login" class="btn">Hi</button>-->
  <h3 v-if="$auth.isAuthenticated">Hi, {{ $auth.user.name }}!</h3>
</div>
    <p>Welcome, Employee! Your first day,uh?<br>
    Please feel free to browse around<br>
    and do not forget to sign into our employee-net</p>
    <img :src="require(`@/assets/home.svg`)"/>
</main>
</template>

<script>


export default {
  name: 'home',
  methods: {
    login(e) {
      e.preventDefault()
      this.$auth.loginWithRedirect();
    }
  }
}
</script>


<style scoped>
h1{
  font-weight: 800;
  color: rgb(4, 4, 39);
  font-size: 2em;
}

p {
  padding: 2%;
}
img {
  width: 50%;
  height: auto;
  padding: 2%;
}
</style>