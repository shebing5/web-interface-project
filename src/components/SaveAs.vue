<template>
  <div class="save-as">
    <h2>Save Chat As</h2>
    <button @click="saveAsMarkdown">Save as Markdown</button>
    <button @click="saveAsImage">Save as Image</button>
    <button @click="saveAsJSON">Save as JSON</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      chatRecords: [],
    };
  },
  methods: {
    saveAsMarkdown() {
      const markdown = this.chatRecords.map(record => `**${record.sender}:** ${record.content}`).join('\n\n');
      const blob = new Blob([markdown], { type: 'text/markdown' });
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url;
      a.download = 'chat-records.md';
      a.click();
      URL.revokeObjectURL(url);
      console.log('Chat records saved as Markdown');
    },
    saveAsImage() {
      // Implement the logic to save chat records as an image
      console.log('Chat records saved as Image');
    },
    saveAsJSON() {
      const dataStr = JSON.stringify(this.chatRecords, null, 2);
      const blob = new Blob([dataStr], { type: 'application/json' });
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url;
      a.download = 'chat-records.json';
      a.click();
      URL.revokeObjectURL(url);
      console.log('Chat records saved as JSON');
    },
  },
};
</script>

<style>
.save-as {
  padding: 20px;
}

button {
  margin-right: 10px;
  padding: 10px;
}
</style>
