<template>
    <div class="message-form">
      <h2>Enviar un missatge</h2>
      <form @submit.prevent="submitMessage">
        <input
          type="text"
          v-model="messageText"
          placeholder="Escriu el teu missatge"
          class="message-input"
        />
        <button type="submit" class="send-button">Enviar</button>
      </form>
    </div>
  </template>
  
  <script setup>
  const props = defineProps({
    author: {
      type: String,
      required: true
    }
  })
  
  import { ref } from 'vue'
  const messageText = ref('')
  
  const emit = defineEmits(['send-message'])
  
  const submitMessage = () => {
    if (messageText.value.trim()) {
      const message = {
        author: props.author,
        text: messageText.value
      }
      emit('send-message', message)
      messageText.value = ''
    }
  }
  </script>
  
  <style scoped>
  .message-form {
    padding: 20px;
    background-color: #e9f5ff;
    border-radius: 10px;
    border: 1px solid #ddd;
  }
  
  .message-input {
    padding: 10px;
    width: 80%;
    margin-right: 10px;
    border-radius: 5px;
    border: 1px solid #ccc;
    font-size: 1em;
  }
  
  .send-button {
    padding: 10px 15px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
    font-size: 1em;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  .send-button:hover {
    background-color: #0056b3;
  }
  
  h2 {
    margin-bottom: 15px;
    color: #333;
  }
  </style>
  