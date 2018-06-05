<template>
    <table v-show="meetings.length > 0">
        <thead>
            <tr>
                <th>Nazwa spotkania</th>
                <th>Opis</th>
                <th>Uczestnicy</th>
                <th></th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="meeting in meetings" :key="meeting.name">
                <td>{{meeting.name}}</td>
                <td>{{meeting.description}}</td>
                <td>
                    <div v-for="participant in meeting.participants" :key="participant">
                        {{participant}}
                    </div>
                </td>
                <td v-if="!meeting.participants.includes(email)" >
                    <button class="button-outline" @click="addMe(meeting)">zapisz sie</button>
                    <button @click="removeEmptyMeeting(meeting)">usun puste spotkanie</button></td>
                <td v-else><button @click="unsubscribeMe(meeting)">wypisz sie</button> 
                    </td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
  props: ["meetings", "email"],
  methods: {
    addMe(meeting) {
      return meeting.participants.push(this.email);
    },
    unsubscribeMe(meeting) {
      return meeting.participants.splice(
        meeting.participants.indexOf(this.email),
        1
      );
    },
    removeEmptyMeeting(meeting) {
      if (meeting.participants.length > 0) {
        //do nothing
      } else {
        this.meetings = this.meetings.splice(this.meetings.indexOf(meeting), 1);
      }
      return this.meetings;
    }
  }
};
</script>