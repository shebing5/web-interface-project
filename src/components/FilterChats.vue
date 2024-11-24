<template>
  <div class="filter-chats">
    <input v-model="searchQuery" @input="filterChats" placeholder="Search chats and folders" />
    <div class="chat-list">
      <div v-for="chat in filteredChats" :key="chat.id" class="chat-item">
        <span class="chat-title">{{ chat.title }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: '',
      chats: [],
      filteredChats: [],
    };
  },
  methods: {
    filterChats() {
      this.filteredChats = this.chats.filter(chat => 
        chat.title.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
  },
  created() {
    // Fetch chats from the server or initialize with some data
    this.chats = [
      { id: 1, title: 'Chat 1' },
      { id: 2, title: 'Chat 2' },
      { id: 3, title: 'Chat 3' },
    ];
    this.filteredChats = this.chats;
  },
};
</script>

<style>
.filter-chats {
  padding: 20px;
}

.chat-list {
  margin-top: 20px;
}

.chat-item {
  margin-bottom: 10px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}
</style>
