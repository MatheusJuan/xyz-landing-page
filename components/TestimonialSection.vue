<script setup lang="ts">
import { defineProps } from 'vue'
import { Star, Users } from 'lucide-vue-next'

defineProps({
  quote: { type: String, default: '' },
  author: { type: Object as () => { name: string, role: string }, default: () => ({ name: '', role: '' }) }
})
</script>

<template>
  <section class="py-16 px-4 bg-gradient-to-r from-[#00ff88]/10 to-transparent">
    <div class="container mx-auto">
      <div class="max-w-4xl mx-auto bg-gray-900/50 border border-[#00ff88]/30 backdrop-blur-sm p-8 rounded-lg">
        <div class="flex justify-center mb-6">
          <Star v-for="i in 5" :key="i" class="w-6 h-6 text-[#00ff88] fill-current" />
        </div>
        <blockquote class="text-xl md:text-2xl text-gray-300 mb-6 italic text-center">
          "{{ quote }}"
        </blockquote>
        <div class="flex items-center justify-center">
          <div class="w-12 h-12 bg-[#00ff88]/20 rounded-full flex items-center justify-center mr-4">
            <Users class="w-6 h-6 text-[#00ff88]" />
          </div>
          <div class="text-left">
            <p class="font-semibold text-white text-lg">{{ author.name }}</p>
            <p class="text-sm text-gray-400">{{ author.role }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template> 