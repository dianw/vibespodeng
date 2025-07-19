<script setup lang="ts">
import { Ollama } from 'ollama'
import { ref, onMounted } from 'vue'

const ollama = new Ollama({ host: 'http://localhost:11434' })
const message = ref('')
const response = ref('')
const loading = ref(false)
const models = ref<string[]>([])
const selectedModel = ref('')
const loadingModels = ref(false)

async function fetchModels() {
  loadingModels.value = true
  try {
    const response = await ollama.list()
    models.value = response.models.map(model => model.name)
    if (models.value.length > 0) {
      selectedModel.value = models.value[0] ?? ''
    }
  } catch (error) {
    console.error('Error fetching models:', error)
  } finally {
    loadingModels.value = false
  }
}

onMounted(() => {
  fetchModels()
})

async function generateResponse() {
  if (!message.value) return
  
  loading.value = true
  response.value = ''
  
  try {
    const stream = await ollama.chat({
      model: selectedModel.value,
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
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700 mb-1">Select Model</label>
          <USelect
            v-model="selectedModel"
            :items="models"
            :loading="loadingModels"
            placeholder="Select a model"
            class="w-full"
          />
        </div>
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
