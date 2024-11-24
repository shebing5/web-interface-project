<template>
  <div class="token-calculator">
    <h2>Token Calculator</h2>
    <div class="input-container">
      <input v-model="message" placeholder="Type a message" />
      <button @click="calculateTokens">Calculate</button>
    </div>
    <div class="result">
      <p>Token Count: {{ tokenCount }}</p>
      <p>Price: ${{ price }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: '',
      tokenCount: 0,
      price: 0,
    };
  },
  methods: {
    calculateTokens() {
      this.tokenCount = this.message.length; // Simple token calculation based on message length
      this.price = this.tokenCount * 0.01; // Example price calculation
    },
  },
};
</script>

<style>
.token-calculator {
  padding: 20px;
}

.input-container {
  display: flex;
  margin-bottom: 20px;
}

input {
  flex: 1;
  padding: 10px;
}

button {
  padding: 10px;
  margin-left: 10px;
}

.result {
  margin-top: 20px;
}
</style>
