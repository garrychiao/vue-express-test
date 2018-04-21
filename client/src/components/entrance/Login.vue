<template>
  <v-container>
    <v-layout row class="pt-5">
      <v-flex xs6 offset-xs3>
        <div class="white elevation-2">
          <v-toolbar flat dense class="cyan" dark>
            <v-toolbar-title>Login</v-toolbar-title>
          </v-toolbar>
          <div class="pl-4 pr-4 pt-2 pb-2">
            <v-layout row>
              <v-flex xs4>
                <v-subheader>Email</v-subheader>
              </v-flex>
              <v-flex xs8>
                <v-text-field
                type="email"
                v-model="email"
                label="Email"
                id="email"
                ></v-text-field>
              </v-flex>
            </v-layout>
            <v-layout row>
              <v-flex xs4>
                <v-subheader>Password</v-subheader>
              </v-flex>
              <v-flex xs8>
                <v-text-field
                type="password"
                v-model="password"
                label="Password"
                id="password"
                ></v-text-field>
              </v-flex>
            </v-layout>

            <div class="error-text" v-html="error"/>
            <v-btn class="cyan" @click="login">Login</v-btn>
          </div>
        </div>
      </v-flex>
    </v-layout>
  </v-container>
</template>
<script>
import AuthenticationService from '@/services/AuthenticationService'
export default {
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async login () {
      try {
        const response = await AuthenticationService.login({
          email: this.email,
          password: this.password
        })
        this.$store.dispatch('setToken', response.data.token)
        this.$store.dispatch('setUser', response.data.user)
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error-text {
  color: red;
}
</style>
