<template>
  <div id="app">
    <Home />
    <VueBotUI
      :messages="messages"
      :options="botOptions"
      :bot-typing="botTyping"
      :input-disable="botTyping"
      @msg-send="messageSendHandler"
    />
  </div>
</template>

<script>
import axios from "axios";
import { VueBotUI } from "vue-bot-ui";
import Home from "@/components/Home.vue";

export default {
  name: "App",
  components: {
    VueBotUI,
    Home,
  },
  data() {
    return {
      messages: [],
      botTyping: false,
      botOptions: {
        botTitle: "Medical ChatBot",
        botAvatarImg: "https://www.shareicon.net/data/512x512/2017/03/27/881590_medical_512x512.png",
        msgBubbleBgUser: "#e79a09",
        boardContentBg: "#151515",
        colorScheme: "#e79a09",
      },
    };
  },
  mounted() {
      this.messages.push({
        agent: "bot",
        type: "text",
        text: "Hello! I'm Medical ChatBot. How can I help you?",
      });
  },
  methods: {
    messageSendHandler(value) {
      this.messages.push({
        agent: "user",
        type: "text",
        text: value.text,
      });

      this.botTyping = true;

      axios.get("http://localhost:5000/?search=" + value.text).then((res) => {
        console.log(res);

        this.messages.push({
          agent: "bot",
          type: "text",
          text: res.data.message,
        });

        this.botTyping = false;
      });
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
}
</style>
