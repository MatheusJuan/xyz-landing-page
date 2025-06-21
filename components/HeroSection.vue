<script setup lang="ts">
import { defineProps } from 'vue'
import { Play, ArrowRight } from 'lucide-vue-next'

defineProps({
  backgroundUrl: { type: String, default: '' },
  badgeText: { type: String, default: '' },
  title: { type: String, default: '' },
  subtitle: { type: String, default: '' },
  ctaPrimary: { type: Object as () => { text: string }, default: () => ({ text: '' }) },
  ctaSecondary: { type: Object as () => { text: string }, default: () => ({ text: '' }) },
  footerText: { type: String, default: '' }
})
</script>

<template>
  <section class="py-20 px-4 relative overflow-hidden min-h-[90vh] flex items-center">
    <!-- Background Dashboard -->
    <div class="absolute inset-0 z-0">
      <img :src="backgroundUrl" alt="Dashboard Background" class="object-cover opacity-10 w-full h-full" />
      <div class="absolute inset-0 bg-gradient-to-r from-black via-black/80 to-transparent"></div>
    </div>

    <div class="container mx-auto relative z-10">
      <div class="max-w-4xl">
        <div class="mb-6 bg-[#00ff88]/20 text-[#00ff88] border-[#00ff88]/30 text-sm font-semibold inline-block px-3 py-1 rounded-full">
         {{ badgeText }}
        </div>

        <h1 class="text-4xl md:text-6xl lg:text-7xl font-bold mb-6 leading-tight" v-html="title"></h1>

        <p class="text-xl md:text-2xl text-gray-300 mb-8 max-w-3xl leading-relaxed" v-html="subtitle"></p>

        <div class="flex flex-col sm:flex-row gap-4 items-center">
          <a href="https://wa.me/5515998557961?text=quero%20vender%2024%20horas%20por%20dia" target="_blank" rel="noopener noreferrer">
            <button
              class="bg-[#00ff88] hover:bg-[#00dd77] text-black font-bold text-lg px-8 py-4 rounded-lg shadow-lg shadow-[#00ff88]/25 flex !items-center"
            >
              <Play class="w-5 h-5 mr-2" />
              {{ ctaPrimary.text }}
            </button>
          </a>
          <a href="https://wa.me/5515998557961?text=quero%20vender%2024%20horas%20por%20dia" target="_blank" rel="noopener noreferrer">
            <button class="text-[#00ff88] hover:text-[#00dd77] font-semibold text-lg underline underline-offset-4 transition-colors flex !items-center">
              {{ ctaSecondary.text }}
              <ArrowRight class="w-4 h-4 inline ml-1" />
            </button>
          </a>
        </div>

        <p class="text-sm text-[#00ff88] mt-6" v-html="footerText"></p>
      </div>
    </div>
  </section>
</template> 