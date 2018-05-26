<template>
   <div>
      <h3>Witaj {{ email }} </h3> 
      <button @click="logout()"> Wyloguj</button>  
   </div>
</template>

<script>
export default {
  props: ["email"], //te infor moze dostac od komponentu zew - rodzica - otwarcie na swiat

  data() {
    return {
      email: "" // na ten stan rodzic ne i moze wplywac
    };
  },

  methods: {
    logout() {
      this.$emit("logout");
    }
  }
};
</script>