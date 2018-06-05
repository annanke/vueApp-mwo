<template>
  <div id="app">

    <h1>System do zapisow na zajecia</h1>
    <div v-if="!authenticatedEmail">
      <login-form @login="logMeIn($event)" :button-label="'Zaloguj sie'"></login-form>
    </div>
    <div v-show="authenticatedEmail">
      <logged-participant @logout="logMeOut($event)" :email="authenticatedEmail"></logged-participant>
      <meeting-page :email="authenticatedEmail"></meeting-page>
    </div>

  </div>
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";
import LoggedParticipant from "./LoggedParticipant";
import MeetingPage from "./meetings/MeetingPage";
export default {
  components: { LoginForm, LoggedParticipant, MeetingPage },
  name: "app",
  data() {
    return {
      authenticatedEmail: ""
    };
  },
  methods: {
    logMeOut() {
      this.authenticatedEmail = "";
    },
    logMeIn(email) {
      this.authenticatedEmail = email;
    }
  }
};
</script>

<style>
.validationError {
  color: red;
  display: inline;
}

h3 {
  display: inline-block;
  width: 65%;
}
</style>
