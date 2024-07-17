<template>
  <div>
      <div v-for="message in messages" :key="message">{{ message }}</div>
      <input v-model="message" @keyup.enter="sendMessage" placeholder="Type your message" />
  </div>
</template>

<script>
export default {
  data() {
      return {
          message: '',
          messages: []
      };
  },
  mounted() {
      window.Echo.channel('chat')
          .listen('MessageSent', (e) => {
              this.messages.push(e.message);
          });
  },
  methods: {
      sendMessage() {
          axios.post('/send-message', {
              message: this.message
          }).then(response => {
              this.message = '';
          });
      }
  }
};
</script>

<style>
  .background {
    height: 100%;
    width: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
</style>