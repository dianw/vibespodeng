<template>
  <div>
    <UContainer>
      <nav class="py-4">
        <UButton
          to="/chat"
          icon="i-heroicons-chat-bubble-left-right"
        >
          Chat with Ollama
        </UButton>
        <UButton
          to="/testing"
          icon="i-heroicons-beaker"
        >
          Testing
        </UButton>
      </nav>
      
      <main>
        <NuxtPage />
      </main>
    </UContainer>
  </div>
</template>

<script setup lang="ts">
// Add page transitions and other app-wide configuration here if needed
</script>
