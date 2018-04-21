<template>
  <v-toolbar fixed>
    <v-toolbar-side-icon></v-toolbar-side-icon>
    <v-toolbar-title><span class="home" @click="navigateTo({name: 'root'})">Title</span></v-toolbar-title>
    <v-toolbar-items class="hidden-sm-and-down">
      <v-btn flat>Browse</v-btn>
    </v-toolbar-items>
    <v-spacer></v-spacer>
    <v-toolbar-items class="hidden-sm-and-down">
      <v-btn v-if="!$store.state.isUserLoggedIn" flat @click="navigateTo({name: 'register'})">
        Sign up
      </v-btn>
      <v-btn v-if="!$store.state.isUserLoggedIn" flat @click="navigateTo({name: 'login'})">
        Login
      </v-btn>
      <!--<router-link to="register" flat>
        Sign up
      </router-link>-->
    </v-toolbar-items>
  </v-toolbar>
</template>
<script>
export default {
  methods: {
    navigateTo (route) {
      this.$router.push(route)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.home {
  cursor: pointer;
}
</style>
