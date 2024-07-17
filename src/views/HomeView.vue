<template>
  <div class="background">
      <div class="visualize">
        <div class="chat-person">
          <p class="other-message"> Olá Jair!! Tudo certim? </p>
        </div>
        <div class="my-chat">
          <p class="messages"> Olá Vitor!! Tudo certim? </p>
        </div>
      </div>
      <input class="input" placeholder="Escreva sua menssagem" />
  </div>
</template>

<script>
import axios from 'axios';


  export default {
    data() {
      return {
        message: '',
        index: 0,
      }
    },
    methods: {
      getMessage() {
        axios.get('https://busy-rings-draw.loca.lt/api/tasks')
          .then ((response) => {
            console.log(response.data[this.index].message);
            this.message = response.data.message;
          })
      }
    },
    created () {
      this.getMessage();
    },
  }
</script>

<style>
  .background {
    height: 100vh;
    width: 100vw;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 10px;
  }
  .visualize {
    height: 90vh;
    width: 70vh;
    background-color: #FFFF;
    display: flex;
    flex-direction: column;
    overflow-y: scroll;
    overflow-x: hidden;
  }

  .input {
    height: 5vh;
    width: 70vh;
    appearance: none;
    border: none;
    outline: none;
    border-bottom: .5em solid #002fff;
    border-radius: .2em .2em 0 0;
    padding: .5em;
    color: #002fff;
  }
 
  .messages {
    color: black;
    padding: 10px;
    background-color: #c9c9c9;
    max-width: 80%;
    margin: 15px;
    display: flex;
    align-items: center;
    justify-content: center;
    word-wrap: break-word;
    overflow-wrap: break-word;
  }
   
  .other-message {
    color: black;
    padding: 10px;
    background-color: #c9c9c9;
    max-width: 80%;
    margin: 15px;
    display: flex;
    align-items: center;
    justify-content: center;
    word-wrap: break-word;
    overflow-wrap: break-word;
  }
  .chat-person {
    max-width: 100%;
    display: flex;
    margin-right: 20%;
  }
  .my-chat {
    max-width: 100%;
    margin-left: 20%;
    display: flex;
    justify-content: end;
  }
</style>