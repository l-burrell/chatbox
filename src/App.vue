<template>
  <div>
    <Messages :messages="message"/>
    <br/>
    <input type="text" placeholder="Enter a message" v-model="newMessage"/>
    <!-- <h3>{{newMessage}}</h3> -->
    <button @click="sendMessage(newMessage)">Send Message</button>
  </div>
</template>

<script>
import Messages from "./components/Messages.vue";
import { db } from "./db";

export default {
  name: "App",
  components: {
    Messages,
  },
  data() {
    return {
      message: [],
      newMessage: '',
    }
  },
  firestore: {
    message: db.collection("messages").orderBy('createdAt'),
  }, 
  methods: {
    sendMessage(newMessage){
      db.collection("messages").add({
        createdAt: new Date(),
        value: newMessage,
        })
      // this.message = [...this.message, newMessage];
      this.newMessage = "";
    },
  },
};
</script>
