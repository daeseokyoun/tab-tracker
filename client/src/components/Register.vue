<template>
  <v-layout column>
    <v-flex xs6 offset-xs3>
      <div class="white elevation-2">
        <v-toolbar flat dense class="cyan" dark>
          <v-toolbar-title>Register</v-toolbar-title>
        </v-toolbar>

        <div class="pl-4 pr-4 pt-4 pb-4">
          <form
            name="tab-tracker-form"
            autocomplete="off">
            <v-text-field
              name="input-10-1"
              label="Email"
              v-model="email"
            ></v-text-field>
            <br>
            <v-text-field
              type="password"
              label="Password"
              v-model="password"
              autocomplete="new-password"
            ></v-text-field>
          </form>
          <br>
          <div class="error" v-html="error"/>
          <br>
          <v-btn class="cyan" dark
            @click="register">
            Register</v-btn>
        </div>
      </div>
    </v-flex>
  </v-layout>
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
    async register () {
      try {
        const response = await AuthenticationService.register({
          email: this.email,
          password: this.password
        })
        console.log(response)
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error {
  color: red;
}

</style>
