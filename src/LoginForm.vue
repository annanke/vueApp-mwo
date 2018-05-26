<template>
   <div>
       <label>Zaloguj sie e-mailem</label>
       <input type="email" v-model="email">
       <button @click="enter()">{{buttonLabelToDisplay}}</button>
   </div>
</template>

<script>
export default {
  props: ["buttonLabel"], //te infor moze dostac od komponentu zew - rodzica - otwarcie na swiat

  data() {
    return {
      email: "" // na ten stan rodzic ne i moze wplywac
    };
  },
  /*  mounted(){
    if(!this.buttonLabel){
      this.buttonLabel ='zaloguj';
    }
 }, */
  computed: {
    buttonLabelToDisplay() {
      return this.buttonLabel || 'Zaloguj sie'
      }
  },
  methods: {
    enter() {
      this.$emit("login", this.email);
    }
  }
};
</script>