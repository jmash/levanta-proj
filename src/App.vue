<template>
    <div>
        <div>
            <AskMessage text="What did you get done today?" :currDate=currDate></AskMessage>
            <UserInput
                v-model="checkInMessage"
                @submit="onCheckIn"
            ></UserInput>
        </div>
        <OthersMessage text="What's everyone else up to?"></OthersMessage> <!-- "what did everyone else do" or something along those lines -->
        <TeamData :mooks="mooks"></TeamData> <!-- show data for other team members -->
    </div>
</template>

<script>

import UserInput from './components/UserInput';
import OthersMessage from './components/OthersMessage';
import AskMessage from './components/AskMessage';
import TeamData from './components/TeamData';

export default {
  name: 'app',
  components: {
    UserInput,
    OthersMessage,
    AskMessage,
    TeamData
  },
  data() {
      return {
        checkInMessage: "",
        currDate: new Date().toLocaleDateString(),
        mooks: [
            {
                name: "Axel Hyanandezzer",
                message: "Drank for 20 hours straight then went to bed slightly buzzed",
                submitTime: new Date('2018-06-18T04:00:00').toLocaleTimeString()
            },
            {
                name: "Big Bear McGillicutty",
                message: "Ate a bear but mostly its hair",
                submitTime: new Date('2018-06-18T03:00:00').toLocaleTimeString()
            },
            {
                name: "John Vogelsong Raptorteeth",
                message: "Destroyed your LIFE",
                submitTime: new Date('2018-06-18T02:00:00').toLocaleTimeString()
            }
        ]
      }
  },
  methods: {
    onCheckIn: function(event) {
        this.addPost(event);
    },
    addPost: function(eventMessage) {
        this.mooks.push({
            name: "Jurrd Hurrd McGurrd",
            message: eventMessage,
            submitTime: new Date().toLocaleTimeString()
        });
    }
  }
}

</script>
