<template>
  <div class="chat-container">
    <div class="messages">
      <div v-for="message in messages" :key="message.id" class="message">
        <span class="sender">{{ message.sender }}:</span>
        <span class="content">{{ message.content }}</span>
      </div>
    </div>
    <div class="input-container">
      <input v-model="newMessage" @keyup.enter="sendMessage" placeholder="Type a message" />
      <button @click="sendMessage">Send</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      messages: [],
      newMessage: '',
    };
  },
  methods: {
    sendMessage() {
      if (this.newMessage.trim() !== '') {
        const message = {
          id: Date.now(),
          sender: 'User',
          content: this.newMessage,
        };
        this.messages.push(message);
        this.newMessage = '';
      }
    },
  },
};
</script>

<style>
.chat-container {
  display: flex;
  flex-direction: column;
  height: 100%;
}

.messages {
  flex: 1;
  overflow-y: auto;
}

.message {
  margin: 10px 0;
}

.sender {
  font-weight: bold;
}

.input-container {
  display: flex;
}

input {
  flex: 1;
  padding: 10px;
}

button {
  padding: 10px;
}
</style>
