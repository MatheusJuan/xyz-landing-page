<script setup lang="ts">
import { defineProps } from 'vue'

defineProps({
  logoUrl: { type: String, default: '' },
  tagline: { type: String, default: '' },
  copyright: { type: String, default: '' }
})
</script>

<template>
  <footer class="bg-black border-t border-gray-800 py-8">
    <div class="container mx-auto px-4 text-center">
      <div class="flex items-center justify-center space-x-3 mb-4">
        <img :src="logoUrl" alt="XYZ Soluciona" class="h-20" />
      </div>
      <p class="text-gray-400 mb-4">{{ tagline }}</p>
      <p class="text-gray-500 text-sm">
        &copy; {{ new Date().getFullYear() }} {{ copyright }}
      </p>
    </div>
  </footer>
</template> 