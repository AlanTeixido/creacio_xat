<template>
  <div class="xat-container">
    <h1>Xat Principal</h1>
    <ul class="message-list">
      <li v-for="(msg, index) in messages" :key="index" class="message-item">
        <strong>{{ msg.author }}:</strong> {{ msg.text }}
      </li>
    </ul>
    <Missatge :author="author" @send-message="addMessage" />
  </div>
</template>

<script setup>
import Missatge from './components/Missatge.vue'

const author = 'Usuari A'
import { ref } from 'vue'
const messages = ref([])

const addMessage = (newMessage) => {
  messages.value.push(newMessage)
}
</script>

<style scoped>
.xat-container {
  margin: 40px auto;
  padding: 20px;
  max-width: 500px;
  border: 2px solid #ddd;
  border-radius: 10px;
  background-color: #f7f7f7;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
}

h1 {
  text-align: center;
  color: #333;
  font-size: 1.8em;
}

.message-list {
  list-style-type: none;
  padding: 0;
  margin-bottom: 20px;
}

.message-item {
  padding: 10px;
  margin: 5px 0;
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
}
</style>
