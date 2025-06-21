<script setup lang="ts">
import { defineProps } from 'vue'
import { CheckCircle } from 'lucide-vue-next'

defineProps({
  imageUrl: { type: String, default: '' },
  badgeText: { type: String, default: '' },
  title: { type: String, default: '' },
  problems: { type: Array as () => { text: string }[], default: () => [] }
})
</script>

<template>
  <section id="problema" class="py-20 px-4 relative">
    <div class="container mx-auto">
      <div class="grid lg:grid-cols-2 gap-16 items-center max-w-7xl mx-auto">
        <!-- Lado esquerdo - Imagem -->
        <div class="relative">
          <img :src="imageUrl" alt="Seu dia a dia se parece com isso?" class="w-full h-auto rounded-lg" />
        </div>

        <!-- Lado direito - Conteúdo -->
        <div>
          <div class="mb-6 bg-[#00ff88]/20 text-[#00ff88] border-[#00ff88]/30 inline-block px-3 py-1 rounded-full text-sm">{{ badgeText }}</div>

          <h2 class="text-4xl md:text-5xl font-bold mb-8 leading-tight" v-html="title"></h2>

          <div class="space-y-6">
            <div v-for="problem in problems" :key="problem.text" class="flex items-start space-x-4">
              <div class="w-6 h-6 bg-[#00ff88] rounded-sm flex items-center justify-center flex-shrink-0 mt-1">
                <CheckCircle class="w-4 h-4 text-black" />
              </div>
              <div>
                <p class="text-lg text-gray-300" v-html="problem.text"></p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template> 