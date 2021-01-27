<template>
  <div id="app">
    <Container>
      <ChatWindow>
        <ChatMessage 
          v-for="(message, i) in messages" 
          v-bind:key="i"
          
          v-bind:username="message.author" 
          v-bind:datetime="message.datetime" 
        >
          {{message.text}}
        </ChatMessage>
      </ChatWindow>
    </Container>
  </div>
</template>

<script>
import ChatMessage from "./components/ChatMessage.vue";
import Container from "./components/Container.vue";
import ChatWindow from "./components/ChatWindow";

export default {
  name: "App",
  components: {
    Container,
    ChatMessage,
    ChatWindow,
  },
  data() {
    return {
      messages: [
        { username: "Ivan", datetime: "21.312.312", text: "dsdsdsd" },
        { username: "Ivan", datetime: "21.312.312", text: "dsdsdsd" },
      ],
    };
  },
  methods: {
    getMessages() {
      this.axios
        .get("http://37.77.104.246/api/chat/getmessages.php")
        .then((response) => {
          this.messages = response.data;
        });
    },
    sendMessages(){
      this.axios
        .post("http://37.77.104.246/api/chat/sendmessage.php")

    }
  },
  mounted() {
    this.getMessages();
  },
};
</script>

<style>
#app {
  body {
    margin: 0;
    background-color: #f9f9fa;
  }
}
</style>
