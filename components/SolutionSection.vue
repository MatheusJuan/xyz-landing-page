<script setup lang="ts">
import { defineProps } from 'vue'
import { Bot, Cloud } from 'lucide-vue-next'

defineProps({
  badgeText: { type: String, default: '' },
  title: { type: String, default: '' },
  subtitle: { type: String, default: '' },
  features: { type: Array as () => { icon: string, title: string, description: string }[], default: () => [] },
  imageUrl: { type: String, default: '' }
})
</script>

<template>
  <section id="solucao" class="py-20 px-4 relative">
    <div class="container mx-auto">
      <div class="grid lg:grid-cols-2 gap-16 items-center max-w-7xl mx-auto">
        <!-- Lado esquerdo - Conteúdo -->
        <div>
          <div class="mb-6 bg-[#00ff88]/20 text-[#00ff88] border-[#00ff88]/30 inline-block px-3 py-1 rounded-full text-sm">{{ badgeText }}</div>

          <h2 class="text-4xl md:text-5xl font-bold mb-8 leading-tight" v-html="title"></h2>

          <p class="text-xl text-gray-300 mb-8 leading-relaxed" v-html="subtitle"></p>

          <div class="grid md:grid-cols-2 gap-8">
            <div v-for="feature in features" :key="feature.title" class="bg-gray-900/50 border border-[#00ff88]/30 hover:border-[#00ff88]/50 transition-all p-6 rounded-lg">
              <div class="w-12 h-12 bg-[#00ff88]/20 rounded-lg flex items-center justify-center mb-4">
                <component :is="feature.icon === 'Bot' ? Bot : Cloud" class="w-6 h-6 text-[#00ff88]" />
              </div>
              <h3 class="text-[#00ff88] text-lg font-bold mb-2">{{ feature.title }}</h3>
              <p class="text-gray-300 text-sm">{{ feature.description }}</p>
            </div>
          </div>
        </div>

        <!-- Lado direito - Imagem da IA -->
        <div class="relative">
          <img :src="imageUrl" alt="IA SDR" class="w-full h-auto rounded-lg" />
        </div>
      </div>
    </div>
  </section>
</template> 