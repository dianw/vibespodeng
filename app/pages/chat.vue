<script setup lang="ts">
import { Ollama } from 'ollama'
import { ref } from 'vue'

const ollama = new Ollama({ host: 'http://localhost:11434' })
const message = ref('')
const response = ref('')
const loading = ref(false)

async function generateResponse() {
  if (!message.value) return
  
  loading.value = true
  response.value = ''
  
  try {
    const stream = await ollama.chat({
      model: 'gemma3:1b',
      messages: [{ role: 'user', content: message.value }],
      stream: true
    })

    for await (const chunk of stream) {
      response.value += chunk.message.content
    }
  } catch (error) {
    console.error('Error:', error)
    response.value = 'Error: Make sure Ollama is running locally on port 11434'
  } finally {
    loading.value = false
  }
}
</script>

<template>
  <div class="p-4 max-w-3xl mx-auto">
    <h1 class="text-2xl font-bold mb-4">Chat with Ollama</h1>
    
    <div class="space-y-4">
      <UCard>
        <UTextarea
          v-model="message"
          :rows="4"
          placeholder="Type your message..."
          class="w-full"
        />
        <UButton
          :loading="loading"
          :disabled="!message || loading"
          @click="generateResponse"
          class="mt-2"
        >
          Send Message
        </UButton>
      </UCard>

      <UCard v-if="response" class="mt-4">
        <div class="prose">
          {{ response }}
        </div>
      </UCard>
    </div>
  </div>
</template>
