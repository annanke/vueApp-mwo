<template>
    <div>
        <!--<button @click="reveal()">Dodaj nowe spotkanie</button> -->
        <button v-on:click="addRequest=!addRequest">Dodaj nowe spotkanie</button>
        <new-meeting-form @added="onNewMeeting($event)" v-if="addRequest"></new-meeting-form>
        <p v-show="meetings[0]">Zaplanowane zajecia ({{meetings.length}})</p>
        <p v-show="!meetings[0]">brak zaplanowanych spotkan</p>

        <meetings-list :meetings="meetings" :email="email"></meetings-list>
    </div>
</template>
<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList"

    export default{
        props: ["email"],
        components: {NewMeetingForm, MeetingsList},
        data(){
            return {
                addRequest: false,
                meetings: []
            };
        },
        methods:{
            onNewMeeting(meeting){
                this.meetings.push(meeting);
                this.addRequest = false;
            },
            reveal(){
                this.addRequest=true;
            }
        }
    }
</script>