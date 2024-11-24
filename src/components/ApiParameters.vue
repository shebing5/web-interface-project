<template>
  <div class="api-parameters">
    <h2>API Parameters</h2>
    <form @submit.prevent="saveParameters">
      <div class="form-group">
        <label for="penalty">Penalty:</label>
        <input type="number" v-model="parameters.penalty" id="penalty" />
      </div>
      <div class="form-group">
        <label for="temperature">Temperature:</label>
        <input type="number" v-model="parameters.temperature" id="temperature" />
      </div>
      <div class="form-group">
        <label for="maxTokens">Max Tokens:</label>
        <input type="number" v-model="parameters.maxTokens" id="maxTokens" />
      </div>
      <button type="submit">Save</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      parameters: {
        penalty: 0,
        temperature: 0.7,
        maxTokens: 100,
      },
    };
  },
  methods: {
    saveParameters() {
      // Save the parameters to the server or local storage
      console.log('Parameters saved:', this.parameters);
    },
  },
};
</script>

<style>
.api-parameters {
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
