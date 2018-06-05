<template>
    <form @submit.prevent="addNewMeeting()">
        <h4>Dodaj nowe spotkanie</h4>
        <label>Nazwa</label>
        <input type="text" v-model="newMeeting.name">
        <label>Opis</label>
        <textarea v-model="newMeeting.description"></textarea>
        <button>Dodaj</button><label class="validationError" v-if="!isValid"> Spotkanie musi miec nazwe!</label>
    </form>
</template>

<script>
export default {
    data(){
        return{
            isValid : true,
            newMeeting:{
                name: "",
                description: "",
                participants: []
            }
        };
    },
    methods: {
        addNewMeeting(){
            if(this.newMeeting.name!=undefined && this.newMeeting.name.length>0){
                this.$emit('added', this.newMeeting);
                this.newMeeting={};
                this.isValid = true;
            }else{
                this.isValid = false;
            }
            
        }
    }
}
</script>
