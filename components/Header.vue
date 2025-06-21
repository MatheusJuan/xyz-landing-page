<script setup lang="ts">
import { defineProps } from 'vue'

defineProps({
  logoUrl: String,
  navLinks: Array as () => { text: string; href: string }[]
})
</script>

<template>
  <header class="border-b border-gray-800 sticky top-0 z-50 bg-black/95 backdrop-blur">
    <div class="container mx-auto px-4 py-4">
      <div class="flex justify-between items-center">
        <div class="flex items-center space-x-3">
          <img :src="logoUrl" alt="XYZ Soluciona" class="h-20" />
        </div>
        <nav class="hidden md:flex space-x-8">
          <a v-for="link in navLinks" :key="link.text" :href="link.href" class="text-gray-300 hover:text-[#00ff88] transition-colors">
            {{ link.text }}
          </a>
        </nav>
        <a href="https://wa.me/5515998557961?text=quero%20vender%2024%20horas%20por%20dia" target="_blank" rel="noopener noreferrer">
          <button class="bg-[#00ff88] hover:bg-[#00dd77] text-black font-semibold py-2 px-4 rounded">Ver Demonstração</button>
        </a>
      </div>
    </div>
  </header>
</template> 