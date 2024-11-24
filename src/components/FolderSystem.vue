<template>
  <div class="folder-system">
    <h2>Folder System</h2>
    <div class="folder-list">
      <div v-for="folder in folders" :key="folder.id" :style="{ backgroundColor: folder.color }" class="folder-item">
        <span class="folder-name">{{ folder.name }}</span>
        <button @click="editFolder(folder.id)">Edit</button>
        <button @click="deleteFolder(folder.id)">Delete</button>
      </div>
    </div>
    <div class="add-folder">
      <input v-model="newFolderName" placeholder="Add a new folder" />
      <input v-model="newFolderColor" type="color" />
      <button @click="addFolder">Add</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      folders: [],
      newFolderName: '',
      newFolderColor: '#ffffff',
    };
  },
  methods: {
    addFolder() {
      if (this.newFolderName.trim() !== '') {
        const folder = {
          id: Date.now(),
          name: this.newFolderName,
          color: this.newFolderColor,
        };
        this.folders.push(folder);
        this.newFolderName = '';
        this.newFolderColor = '#ffffff';
      }
    },
    editFolder(id) {
      const folder = this.folders.find(f => f.id === id);
      if (folder) {
        const newName = prompt('Edit folder name:', folder.name);
        const newColor = prompt('Edit folder color:', folder.color);
        if (newName !== null) {
          folder.name = newName;
        }
        if (newColor !== null) {
          folder.color = newColor;
        }
      }
    },
    deleteFolder(id) {
      this.folders = this.folders.filter(f => f.id !== id);
    },
  },
};
</script>

<style>
.folder-system {
  padding: 20px;
}

.folder-list {
  margin-bottom: 20px;
}

.folder-item {
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
  padding: 10px;
  border-radius: 5px;
}

.add-folder {
  display: flex;
}

input[type="text"] {
  flex: 1;
  padding: 10px;
}

input[type="color"] {
  margin-left: 10px;
}

button {
  padding: 10px;
  margin-left: 10px;
}
</style>
