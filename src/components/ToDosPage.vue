<template>
   <div class="App">
      <header class="App-header">
        <div class="Api-key">
          <span>Enter API key from email: </span>
          <input
            class="Api-input"
            type="text"
            v-model="apiKey"
          />
        </div>
        <div class="Todo-list">
          <span>No items</span>
        </div>
      </header>
    </div>
</template>

<script>
const apiKeyLocalStorageKey = "API_KEY_LOCAL_STORAGE"

export default {
  data() {
    return {
      apiKey: localStorage.getItem(apiKeyLocalStorageKey)
    }
  },
  methods: {
    storeAPIPasswordInLocalStorage() {
      localStorage.setItem(
        apiKeyLocalStorageKey,
        this.apiKey
      );
    }
  },
  watch: {
        apiKey: function parsedInput() {
            console.log("Watch")
            this.storeAPIPasswordInLocalStorage()
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.Todo-list {
  background: #e8e8e8;
  border-radius: 4px;
  margin: 10px;
  padding: 10px;
}

.Api-key {
  background: #ffffff;
  border-radius: 4px;
  margin: 10px;
  padding: 3px 10px;
}

.App {
  background: #209cee;
  height: 100vh;
  padding: 1rem 20rem;
  display: flex;
  flex-direction: column;
}

.App-header {
  align-items: center;
  justify-content: center;
  font-size: 1.2em;
  color: rgb(0, 0, 0);
}

.Api-input {
  width: 20rem;
  padding-top: 2px;
}

.App-todo-item {
  text-align: left;
  align-items: center;
  background: #fff;
  border-radius: 5px;
  box-shadow: 1px 1px 1px rgba(0, 0, 0, 0.15);
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
  padding: 15px 10px;
}
</style>
