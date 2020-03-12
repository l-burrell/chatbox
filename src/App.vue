<template>
  <div id="app">
    <Messages :messages="message"/>
    <div id="send">
      <input id="msg" class="py-2" type="text" placeholder="Enter a message" v-model="newMessage"/>
      <button class="bg-red-500 font-bold text-white py-2 px-4" @click="sendMessage(newMessage)">Send Message</button>
    </div>
  </div>
</template>

<style scoped>
  #send {
    margin: auto;
    width: 500px;
    padding: 20px;
  }
  #msg {
    width: 320px;
    padding: 4px;
    /* border: solid black 2px; */
  }
  #app {
    /* background-color: #333;; */
  }
</style>

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