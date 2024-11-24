<template>
  <div class="edit-messages">
    <h2>Edit Messages</h2>
    <div class="message-list">
      <div v-for="(message, index) in messages" :key="message.id" class="message-item">
        <span class="message-content">{{ message.content }}</span>
        <button @click="editMessage(index)">Edit</button>
        <button @click="deleteMessage(index)">Delete</button>
        <button @click="moveMessageUp(index)" :disabled="index === 0">Up</button>
        <button @click="moveMessageDown(index)" :disabled="index === messages.length - 1">Down</button>
      </div>
    </div>
    <div class="add-message">
      <input v-model="newMessageContent" placeholder="Add a new message" />
      <button @click="addMessage">Add</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      messages: [],
      newMessageContent: '',
    };
  },
  methods: {
    addMessage() {
      if (this.newMessageContent.trim() !== '') {
        const message = {
          id: Date.now(),
          content: this.newMessageContent,
        };
        this.messages.push(message);
        this.newMessageContent = '';
      }
    },
    editMessage(index) {
      const newContent = prompt('Edit message content:', this.messages[index].content);
      if (newContent !== null) {
        this.messages[index].content = newContent;
      }
    },
    deleteMessage(index) {
      this.messages.splice(index, 1);
    },
    moveMessageUp(index) {
      if (index > 0) {
        const temp = this.messages[index];
        this.messages.splice(index, 1);
        this.messages.splice(index - 1, 0, temp);
      }
    },
    moveMessageDown(index) {
      if (index < this.messages.length - 1) {
        const temp = this.messages[index];
        this.messages.splice(index, 1);
        this.messages.splice(index + 1, 0, temp);
      }
    },
  },
};
</script>

<style>
.edit-messages {
  padding: 20px;
}

.message-list {
  margin-bottom: 20px;
}

.message-item {
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
  padding: 10px;
  border-radius: 5px;
  background-color: #f0f0f0;
}

.add-message {
  display: flex;
}

input {
  flex: 1;
  padding: 10px;
}

button {
  padding: 10px;
  margin-left: 10px;
}
</style>
