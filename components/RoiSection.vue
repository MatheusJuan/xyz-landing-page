<script setup lang="ts">
import { defineProps } from 'vue'

defineProps({
  badgeText: { type: String, default: '' },
  title: { type: String, default: '' },
  subtitle: { type: String, default: '' },
  projection: {
    type: Object as () => {
      title: string,
      headers: string[],
      rows: (string | number)[][]
    },
    default: () => ({ title: '', headers: [], rows: [] })
  },
  comparison: {
    type: Object as () => {
      title: string,
      headers: string[],
      rows: (string | number)[][]
    },
    default: () => ({ title: '', headers: [], rows: [] })
  }
})
</script>

<template>
  <section id="roi" class="py-20 px-4 relative">
    <div class="absolute inset-0 bg-gradient-to-br from-[#00ff88]/5 to-transparent"></div>

    <div class="container mx-auto relative z-10">
      <div class="text-center mb-16">
        <div class="mb-4 bg-[#00ff88]/20 text-[#00ff88] border-[#00ff88]/30 inline-block px-3 py-1 rounded-full text-sm">{{ badgeText }}</div>
        <h2 class="text-4xl md:text-5xl font-bold mb-6" v-html="title"></h2>
        <p class="text-xl text-gray-300 max-w-3xl mx-auto" v-html="subtitle"></p>
      </div>

      <!-- Tabela de Projeção -->
      <div class="mb-16">
        <h3 class="text-3xl font-bold text-center mb-8 text-[#00ff88]">{{ projection.title }}</h3>
        <div class="max-w-5xl mx-auto">
          <div class="bg-gray-900/50 border border-[#00ff88]/30 overflow-hidden rounded-lg">
            <div class="overflow-x-auto">
              <table class="w-full">
                <thead class="bg-[#00ff88]/10 border-b border-[#00ff88]/30">
                  <tr>
                    <th v-for="header in projection.headers" :key="header" class="text-left p-4 text-[#00ff88] font-semibold" :class="{'text-center': header !== 'Métrica', 'text-red-400': header.includes('Atual'), 'text-white': header === 'Resultado'}">{{ header.replace(' (Sem IA)', '') }}</th>
                  </tr>
                </thead>
                <tbody class="text-gray-300">
                  <tr v-for="(row, index) in projection.rows" :key="index" class="border-b border-gray-700" :class="{'bg-gray-900/30': index % 2 === 0, 'bg-[#00ff88]/10 border border-[#00ff88]/30': row[0] === 'Vendas Potenciais'}">
                    <td v-for="(cell, cellIndex) in row" :key="cellIndex" class="p-4" :class="{'font-medium': cellIndex === 0, 'text-center': cellIndex > 0, 'text-red-400': cellIndex === 1, 'text-[#00ff88] font-bold': cellIndex === 2, 'text-white font-bold': cellIndex === 3, 'text-lg': row[0] === 'Vendas Potenciais' && cellIndex > 1 }">{{ cell }}</td>
                  </tr>
                </tbody>
              </table>
            </div>
          </div>
        </div>
      </div>

      <!-- Tabela de Comparativo -->
      <div>
        <h3 class="text-3xl font-bold text-center mb-8 text-[#00ff88]">{{ comparison.title }}</h3>
        <div class="max-w-5xl mx-auto">
          <div class="bg-gray-900/50 border border-[#00ff88]/30 overflow-hidden rounded-lg">
            <div class="overflow-x-auto">
              <table class="w-full">
                <thead class="bg-[#00ff88]/10 border-b border-[#00ff88]/30">
                  <tr>
                    <th v-for="header in comparison.headers" :key="header" class="p-4 font-semibold" :class="{'text-left text-[#00ff88]': header === 'Custo Mensal', 'text-center text-[#00ff88]': header === 'IA SDR XYZ', 'text-center text-red-400': header.includes('Humano'), 'text-center text-orange-400': header.includes('Concorrentes')}">{{ header }}</th>
                  </tr>
                </thead>
                <tbody class="text-gray-300">
                   <tr v-for="(row, index) in comparison.rows" :key="index" class="border-b border-gray-700" :class="{'bg-[#00ff88]/5': index === 0}">
                    <td v-for="(cell, cellIndex) in row" :key="cellIndex" class="p-4" :class="{'font-medium': cellIndex === 0, 'text-center': cellIndex > 0, 'text-[#00ff88] font-bold text-lg bg-[#00ff88]/10 border-l border-r border-[#00ff88]/30': cellIndex === 1, 'text-red-400': cellIndex === 2, 'text-orange-400': cellIndex === 3, 'text-sm font-bold': index === 1}">{{ cell }}</td>
                  </tr>
                </tbody>
              </table>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template> 