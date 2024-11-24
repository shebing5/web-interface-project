<template>
  <div class="user-identity">
    <h2>User Identity</h2>
    <form @submit.prevent="saveIdentity">
      <div class="form-group">
        <label for="user">User:</label>
        <input type="text" v-model="identity.user" id="user" />
      </div>
      <div class="form-group">
        <label for="assistant">Assistant:</label>
        <input type="text" v-model="identity.assistant" id="assistant" />
      </div>
      <div class="form-group">
        <label for="system">System:</label>
        <input type="text" v-model="identity.system" id="system" />
      </div>
      <button type="submit">Save</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      identity: {
        user: '',
        assistant: '',
        system: '',
      },
    };
  },
  methods: {
    saveIdentity() {
      // Save the identity to the server or local storage
      console.log('Identity saved:', this.identity);
    },
  },
};
</script>

<style>
.user-identity {
  padding: 20px;
}

.form-group {
  margin-bottom: 20px;
}

label {
  display: block;
  margin-bottom: 5px;
}

input {
  width: 100%;
  padding: 10px;
  box-sizing: border-box;
}

button {
  padding: 10px 20px;
}
</style>
