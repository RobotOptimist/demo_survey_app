<template>
  <b-container class="pt-5">
    <b-row align-h="center" class="mt-5">
      <b-col cols="*">
        <h1 class="title">Fire Hydrant Surveyor</h1>
        <p><em v-if="$nuxt.isOffline">You are offline</em></p>
      </b-col>
    </b-row>
    <b-row align-h="center" v-if="$auth.loggedIn">
      <b-col sm="9" class="my-4">
        <survey-form @submitForm="handleFormResult"></survey-form>
      </b-col>
    </b-row>
    <b-row align-h="center" class="mt-3">
      <b-col cols="*">
        <b-button v-if="!$auth.loggedIn" variant="primary" size="lg" @click="login">Login</b-button>
        <b-button v-else variant="warning" @click="logout" size="lg">Logout</b-button>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import surveyForm from '../components/survey-form'
import { mapGetters } from "vuex";
export default {
  components: {
    surveyForm
  },
  methods: {
    login() {
      this.$auth.loginWith("auth0");
    },
    logout() {
      this.$auth.logout();
    },
    async handleFormResult(formObj) {
      //https://jsonplaceholder.typicode.com/posts is a test API I'm borrowing 
      //I'm making the data fit because I'm too lazy to make my own test API
      const post = {
        title: formObj.serialNumber,
        body: formObj.condition,
        userId: 1
      }
      try {
        const result = await this.$axios.$post('https://jsonplaceholder.typicode.com/posts', post);
        console.log(result);
      } catch(e) {
        console.log(e);
      }
    }
  },
  computed: mapGetters(["isAuthenticated"]),
};
</script>