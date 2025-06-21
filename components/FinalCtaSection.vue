<script setup lang="ts">
import { defineProps, ref, computed } from 'vue'
import { Calendar, CheckCircle } from 'lucide-vue-next'

defineProps({
  backgroundUrl: { type: String, default: '' },
  badgeText: { type: String, default: '' },
  title: { type: String, default: '' },
  subtitle: { type: String, default: '' },
  form: {
    type: Object as () => {
      placeholders: { name: string, email: string, phone: string },
      buttonText: string,
      note: string,
      benefits: string[]
    },
    default: () => ({
      placeholders: { name: '', email: '', phone: '' },
      buttonText: '',
      note: '',
      benefits: []
    })
  },
  privacyText: { type: String, default: '' }
})

const name = ref('')
const email = ref('')
const phone = ref('')

const whatsappUrl = computed(() => {
  const base = 'https://wa.me/5515998557961'
  const message = `Olá! Tenho interesse e gostaria de mais informações. Meu nome é ${name.value}, e-mail: ${email.value}, telefone: ${phone.value}.`
  return `${base}?text=${encodeURIComponent(message)}`
})
</script>

<template>
  <section id="demo" class="py-20 px-4 relative">
    <div class="absolute inset-0 z-0">
      <img :src="backgroundUrl" alt="Growth Engine Background" class="object-cover opacity-10 w-full h-full" />
      <div class="absolute inset-0 bg-gradient-to-t from-black via-black/80 to-transparent"></div>
    </div>

    <div class="container mx-auto relative z-10">
      <div class="max-w-4xl mx-auto text-center">
        <div class="mb-6 bg-[#00ff88]/20 text-[#00ff88] border-[#00ff88]/30 inline-block px-3 py-1 rounded-full text-sm">{{ badgeText }}</div>

        <h2 class="text-4xl md:text-5xl font-bold mb-6" v-html="title"></h2>

        <p class="text-xl text-gray-300 mb-8 max-w-3xl mx-auto" v-html="subtitle"></p>

        <div class="bg-gray-900/80 border border-[#00ff88]/30 backdrop-blur-sm max-w-2xl mx-auto p-8 rounded-lg">
          <div class="space-y-6">
            <div class="grid md:grid-cols-2 gap-4">
              <div>
                <input v-model="name" :placeholder="form.placeholders.name" class="bg-gray-800 border-gray-600 text-white placeholder-gray-400 h-12 focus:border-[#00ff88] w-full px-4 rounded-lg" />
              </div>
              <div>
                <input v-model="email" type="email" :placeholder="form.placeholders.email" class="bg-gray-800 border-gray-600 text-white placeholder-gray-400 h-12 focus:border-[#00ff88] w-full px-4 rounded-lg" />
              </div>
            </div>
            <div>
              <input v-model="phone" :placeholder="form.placeholders.phone" class="bg-gray-800 border-gray-600 text-white placeholder-gray-400 h-12 focus:border-[#00ff88] w-full px-4 rounded-lg" />
            </div>
            <a :href="whatsappUrl" target="_blank" rel="noopener noreferrer">
              <button type="button" class="w-full bg-[#00ff88] hover:bg-[#00dd77] text-black font-bold text-lg py-4 rounded-lg shadow-lg shadow-[#00ff88]/25 flex items-center justify-center">
                <Calendar class="w-5 h-5 mr-2" />
                {{ form.buttonText }}
              </button>
            </a>
            <p class="text-sm text-gray-400 text-center mt-6">{{ form.note }}</p>
          </div>

          <div class="flex items-center justify-center mt-6 space-x-6 text-sm text-gray-400">
            <div v-for="benefit in form.benefits" :key="benefit" class="flex items-center">
              <CheckCircle class="w-4 h-4 text-[#00ff88] mr-2" />
              <span>{{ benefit }}</span>
            </div>
          </div>
        </div>

        <p class="text-gray-500 mt-8 text-sm">
          {{ privacyText }}
        </p>
      </div>
    </div>
  </section>
</template> 