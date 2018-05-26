<template>
  <div id="app">

    <h1>System do zapisow na zajecia</h1>
    <div v-if="!authenticatedEmail">
      <login-form @login="logMeIn($event)" :button-label="'Wejdz'"></login-form>
    </div>
    <div v-else>
      <logged-participant @logout="logMeOut($event)" :email="authenticatedEmail"></logged-participant>
      <meeting-page></meeting-page>
    </div>

  </div>
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";
import LoggedParticipant from "./LoggedParticipant";
import MeetingPage from "./meetings/MeetingPage";
export default {
  components: {LoginForm, LoggedParticipant, MeetingPage},
  name: 'app',
  data () {
    return {

      authenticatedEmail : ''
    }
   },
   methods: {

      logMeOut(){
        this.authenticatedEmail = '';
      },
      logMeIn(email) {
          this.authenticatedEmail = email;
          
      }
  }

}


</script>
/* 
<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
 */