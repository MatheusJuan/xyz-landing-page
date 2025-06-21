<script setup lang="ts">
import { defineProps } from 'vue'
import { Calendar } from 'lucide-vue-next'

defineProps({
  badgeText: { type: String, default: '' },
  title: { type: String, default: '' },
  highlightedText: { type: String, default: '' },
  ctaPrimary: { type: Object as () => { text: string }, default: () => ({ text: '' }) },
  ctaSecondary: { type: Object as () => { text: string }, default: () => ({ text: '' }) },
  imageUrl: { type: String, default: '' }
})
</script>

<template>
  <section class="py-20 px-4 relative">
    <div class="container mx-auto">
      <div class="grid lg:grid-cols-2 gap-16 items-center max-w-7xl mx-auto">
        <!-- Lado esquerdo - Conteúdo -->
        <div>
          <div class="mb-6 bg-[#00ff88]/20 text-[#00ff88] border-[#00ff88]/30 inline-block px-3 py-1 rounded-full text-sm">{{ badgeText }}</div>

          <h2 class="text-4xl md:text-6xl font-bold mb-8 leading-tight" v-html="title"></h2>

          <div class="border border-[#00ff88]/30 bg-[#00ff88]/5 p-6 rounded-lg mb-8">
            <p class="text-lg text-gray-300 text-center" v-html="highlightedText"></p>
          </div>

          <div class="flex flex-col sm:flex-row gap-4">
            <button class="bg-[#00ff88] hover:bg-[#00dd77] text-black font-bold text-lg px-8 py-4 rounded-lg flex items-center">
              <Calendar class="w-5 h-5 mr-2" />
              {{ ctaPrimary.text }}
            </button>
            <button class="border border-[#00ff88] text-[#00ff88] hover:bg-[#00ff88]/10 font-semibold px-8 py-4 rounded-lg">
              {{ ctaSecondary.text }}
            </button>
          </div>
        </div>

        <!-- Lado direito - Imagem -->
        <div class="relative">
          <img :src="imageUrl" alt="Você está pronto para crescer?" class="w-full h-auto rounded-lg" />
        </div>
      </div>
    </div>
  </section>
</template> 