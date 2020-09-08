<template>
  <div class="container">
    <div>
      <h1 class="title">
        Fire Hydrant Surveyor
      </h1>
      <div class="links">
        <b-button
          v-if="!$auth.loggedIn"
          variant="primary"
          size="lg"
          @click="login"
        >
          Login
        </b-button>
        <b-button
          v-else
          variant="warning"
          @click="logout"
          size="lg"
        >
          Logout
        </b-button>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
export default {
  methods: {
    login() {
      this.$auth.loginWith('auth0')
    },
    logout() {
      this.$auth.logout();
    }
  },
  computed: mapGetters(['isAuthenticated']),
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
