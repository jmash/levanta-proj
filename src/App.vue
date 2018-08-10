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
        <TeamData :mooks="mooks" @removePost="removePost"></TeamData> <!-- show data for other team members -->
    </div>
</template>

<script>

import Vue from 'vue';
//import 

// components
import UserInput from './components/UserInput';
import OthersMessage from './components/OthersMessage';
import AskMessage from './components/AskMessage';
import TeamData from './components/TeamData';
// end components

// firebase
import Firebase from 'firebase';
import VueFirestore from 'vue-firestore';
import fbConfig from './helpers/firebaseConfig.js';

Vue.use(VueFirestore);

Firebase.initializeApp({
    apiKey: fbConfig.apiKey,
    authDomain: fbConfig.authDomain,
    projectId: fbConfig.projectId
});


const firestore = Firebase.firestore();
const settings = {
    timestampsInSnapshots: true
};

firestore.settings(settings);
// end firebase

export default {
  name: 'app',
  components: {
    UserInput,
    OthersMessage,
    AskMessage,
    TeamData
  },
  firestore() {
    return {
        mooks: firestore.collection('mooks')
    }
  },
  data() {
      return {
        checkInMessage: "",
        currDate: new Date().toLocaleDateString(),
      }
  },
  methods: {
    onCheckIn: function(event) {
        this.addPost(event);
        this.checkInMessage = "";
    },
    addPost: function(eventMessage) {
        this.$firestore.mooks.add({
            name: "Jurrd Hurrd McGurrd",
            message: eventMessage,
            submitTime: new Date()
        });
    },
    removePost: function(postId) {
        this.$firestore.mooks.doc(postId).delete();
    },
  }
}

</script>
