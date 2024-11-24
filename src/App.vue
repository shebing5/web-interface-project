<template>
  <div id="app">
    <nav>
      <ul>
        <li><router-link to="/">Home</router-link></li>
        <li><router-link to="/chat">Chat</router-link></li>
        <li><router-link to="/prompt-library">Prompt Library</router-link></li>
        <li><router-link to="/folders">Folders</router-link></li>
        <li><router-link to="/filter-chats">Filter Chats</router-link></li>
        <li><router-link to="/token-calculator">Token Calculator</router-link></li>
        <li><router-link to="/share-chat">Share Chat</router-link></li>
        <li><router-link to="/api-parameters">API Parameters</router-link></li>
        <li><router-link to="/user-identity">User Identity</router-link></li>
        <li><router-link to="/edit-messages">Edit Messages</router-link></li>
        <li><router-link to="/chat-title-generator">Chat Title Generator</router-link></li>
        <li><router-link to="/auto-save">Auto Save</router-link></li>
        <li><router-link to="/import-export">Import/Export</router-link></li>
        <li><router-link to="/save-as">Save As</router-link></li>
      </ul>
    </nav>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App',
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

nav ul {
  list-style-type: none;
  padding: 0;
}

nav li {
  display: inline;
  margin-right: 10px;
}
</style>
