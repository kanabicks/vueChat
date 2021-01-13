<template>
  <div id="app">
    <ChatWindow>
      <chat-message v-for="(message,i ) in messages" v-bind:key="i" username="Ivan" time="21.31.3434 21:21">
    <Container><chat-message v-bind:username="kanabicks" datetime="11.111.2212">Hello!</chat-message></Container>
      </chat-message>
    </ChatWindow>
  </div>
</template>

<script>
import ChatMessage from './components/ChatMessage.vue'
import Container from './components/Container.vue'
import ChatWindow from './components/ChatWindow'

export default {
  name: 'App',
  components: {
    Container,
    ChatMessage,
    ChatWindow
  },
  data(){
   // messages:[
   //   {username: 'Ivan', datetime: '21.312.312' , text: 'dsdsdsd'},
   //   {username: 'Ivan', datetime: '21.312.312' , text: 'dsdsdsd'}
   // ]

  },
  methods:{
    getMessages(){
      this.axios.get('http://37.77.104.246/api/chat/getmessages.php')
      .then((response)=>{
        this.messages=response.data;
      })
    }
  },
  mounted(){
     this.getMessages();
  }
}
</script>

<style>
#app {

body {
  margin: 0;
  background-color: #f9f9fa;
}

}
</style>
