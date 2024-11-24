<template>
  <div class="share-chat">
    <h2>Share Chat</h2>
    <div class="chat-list">
      <div v-for="chat in chats" :key="chat.id" class="chat-item">
        <span class="chat-title">{{ chat.title }}</span>
        <button @click="shareChat(chat.id)">Share</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      chats: [],
    };
  },
  methods: {
    shareChat(id) {
      const chat = this.chats.find(c => c.id === id);
      if (chat) {
        const shareData = {
          title: chat.title,
          text: chat.content,
          url: window.location.href,
        };
        navigator.share(shareData).then(() => {
          console.log('Chat shared successfully');
        }).catch((error) => {
          console.error('Error sharing chat:', error);
        });
      }
    },
  },
  created() {
    // Fetch chats from the server or local storage
    this.chats = [
      { id: 1, title: 'Chat 1', content: 'This is the first chat' },
      { id: 2, title: 'Chat 2', content: 'This is the second chat' },
    ];
  },
};
</script>

<style>
.share-chat {
  padding: 20px;
}

.chat-list {
  margin-bottom: 20px;
}

.chat-item {
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
  padding: 10px;
  border-radius: 5px;
  background-color: #f0f0f0;
}

button {
  padding: 10px;
}
</style>
