<template>
  <div class="prompt-library">
    <h2>Prompt Library</h2>
    <div class="prompt-list">
      <div v-for="prompt in prompts" :key="prompt.id" class="prompt-item">
        <span class="prompt-content">{{ prompt.content }}</span>
        <button @click="editPrompt(prompt.id)">Edit</button>
        <button @click="deletePrompt(prompt.id)">Delete</button>
      </div>
    </div>
    <div class="add-prompt">
      <input v-model="newPrompt" placeholder="Add a new prompt" />
      <button @click="addPrompt">Add</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      prompts: [],
      newPrompt: '',
    };
  },
  methods: {
    addPrompt() {
      if (this.newPrompt.trim() !== '') {
        const prompt = {
          id: Date.now(),
          content: this.newPrompt,
        };
        this.prompts.push(prompt);
        this.newPrompt = '';
      }
    },
    editPrompt(id) {
      const prompt = this.prompts.find(p => p.id === id);
      if (prompt) {
        const newContent = prompt('Edit prompt:', prompt.content);
        if (newContent !== null) {
          prompt.content = newContent;
        }
      }
    },
    deletePrompt(id) {
      this.prompts = this.prompts.filter(p => p.id !== id);
    },
  },
};
</script>

<style>
.prompt-library {
  padding: 20px;
}

.prompt-list {
  margin-bottom: 20px;
}

.prompt-item {
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
}

.add-prompt {
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
