<script setup lang="ts">
import Header from '~/components/Header.vue'
import HeroSection from '~/components/HeroSection.vue'
import ProblemSection from '~/components/ProblemSection.vue'
import SolutionSection from '~/components/SolutionSection.vue'
import RoiSection from '~/components/RoiSection.vue'
import GrowthCtaSection from '~/components/GrowthCtaSection.vue'
import TestimonialSection from '~/components/TestimonialSection.vue'
import FinalCtaSection from '~/components/FinalCtaSection.vue'
import Footer from '~/components/Footer.vue'

const pageData = {
  header: {
    logoUrl: '/images/logo-site.png',
    navLinks: [
      { text: 'O Problema', href: '#problema' },
      { text: 'A Solução', href: '#solucao' },
      { text: 'ROI', href: '#roi' },
      { text: 'Demo', href: '#demo' }
    ]
  },
  hero: {
    backgroundUrl: '/images/Camada 13rww.png',
    badgeText: '🚀 CHEGOU O FIM DO CAOS OPERACIONAL!',
    title: 'Sua equipe está <span class="text-red-400">sobrecarregada</span> e você continua<span class="text-red-400"> perdendo vendas</span>?',
    subtitle: 'Apresentamos a <span class="text-[#00ff88] font-bold">IA SDR</span>: um assistente que <span class="text-[#00ff88] font-bold">trabalha 24/7 para sua empresa</span>, qualificando leads e vendendo no piloto automático.',
    ctaPrimary: { text: 'Ver Demonstração' },
    ctaSecondary: { text: 'Descobrir Como Funciona' },
    footerText: '✅ Demonstração gratuita • ✅ Sem compromisso • ✅ Resultados em 15 minutos'
  },
  problem: {
    imageUrl: 'https://placehold.co/600x800/1f2937/ffffff?text=Problemas',
    badgeText: 'A QUESTÃO É:',
    title: 'SEU <span class="text-[#00ff88]">DIA A DIA</span> SE<br />PARECE COM ISSO?',
    problems: [
      { text: '<span class="text-white font-semibold">Leads esfriando no WhatsApp</span> por falta de resposta rápida.' },
      { text: '<span class="text-white font-semibold">Vendedores gastando mais tempo</span> agendando do que vendendo.' },
      { text: '<span class="text-white font-semibold">Orçamentos que demoram horas</span> (ou dias) para serem enviados.' },
      { text: '<span class="text-white font-semibold">Perda de oportunidades</span> nos fins de semana e feriados.' }
    ]
  },
  solution: {
    badgeText: 'A SOLUÇÃO:',
    title: 'CHEGOU O <span class="text-[#00ff88]">FIM DO</span><br /><span class="text-[#00ff88]">CAOS OPERACIONAL!</span>',
    subtitle: 'Apresentamos a <span class="text-[#00ff88] font-bold">IA SDR</span>: um assistente que <span class="text-[#00ff88] font-bold">trabalha 24/7 para sua empresa</span>',
    features: [
      { icon: 'Bot', title: 'Agente de IA', description: 'Não é um chatbot. É um especialista digital treinado com os dados do seu negócio.' },
      { icon: 'Cloud', title: 'SaaS Completo', description: 'Plataforma completa, sem instalação. Você paga e usa imediatamente.' }
    ],
    imageUrl: 'https://placehold.co/600x800/1f2937/ffffff?text=Solu%C3%A7%C3%A3o'
  },
  roi: {
    badgeText: '💰 FOCO EM RESULTADOS',
    title: 'SOMOS UMA <span class="text-[#00ff88]">GROWTH ENGINE</span>',
    subtitle: 'Queremos <span class="text-[#00ff88] font-semibold">resolver seus problemas</span> para seu negócio <span class="text-[#00ff88] font-semibold underline">evoluir</span>.',
    projection: {
      title: 'Projeção de Ganhos',
      headers: ['Métrica', 'Cenário Atual (Sem IA)', 'Com IA SDR XYZ', 'Resultado'],
      rows: [
        ['Leads Atendidos/Mês', 100, 250, '+150%'],
        ['Taxa de Qualificação', '20%', '35%', '+75%'],
        ['Custo por Lead Qualificado', 'R$ 50,00', 'R$ 18,00', '-64%'],
        ['Vendas Potenciais', 20, 87, '+335%']
      ]
    },
    comparison: {
      title: 'Compare: IA SDR vs. Alternativas',
      headers: ['Custo Mensal', 'IA SDR XYZ', '1 SDR Humano', 'Concorrentes'],
      rows: [
        ['Valor', 'A partir de R$ 497', '> R$ 4.000 + encargos', 'R$ 2.500+ limitado'],
        ['Disponibilidade', '24/7/365', '8h/dia útil', '24/7 limitado']
      ]
    }
  },
  growthCta: {
    badgeText: 'A QUESTÃO É:',
    title: '<span class="text-white">VOCÊ ESTÁ</span><br /><span class="text-white">PRONTO PARA</span><br /><span class="text-[#00ff88]">CRESCER?</span>',
    highlightedText: '<span class="text-white font-semibold">FALE COM UM ESPECIALISTA</span> E ATIVE<br />SEU SDR COM <span class="text-[#00ff88] font-bold">IA HOJE MESMO</span>.',
    ctaPrimary: { text: 'Falar com Especialista' },
    ctaSecondary: { text: 'Ver Demonstração' },
    imageUrl: 'https://placehold.co/600x800/1f2937/ffffff?text=Crescer%3F'
  },
  testimonial: {
    quote: 'Desde que implementamos a IA SDR da XYZ, nosso custo por lead caiu 40% e a capacidade de atendimento triplicou. Em 30 dias, já tínhamos pago o investimento.',
    author: { name: 'Marina Santos', role: 'Diretora Comercial, VendaMais Tech' }
  },
  finalCta: {
    backgroundUrl: 'https://placehold.co/1920x1080/000000/ffffff?text=.',
    badgeText: 'FOCO EM RESULTADOS',
    title: 'SOMOS UMA <span class="text-[#00ff88]">GROWTH ENGINE</span>',
    subtitle: 'Queremos <span class="text-[#00ff88] font-semibold">resolver seus problemas</span> para seu negócio <span class="text-[#00ff88] font-semibold underline">evoluir</span>.',
    form: {
      placeholders: { name: 'Seu nome completo', email: 'Seu melhor e-mail', phone: 'WhatsApp (com DDD)' },
      buttonText: 'ATIVAR MEU SDR COM IA AGORA',
      note: '✅ Rápido, sem compromisso e dura apenas 15 minutos',
      benefits: ['100% Gratuito', 'Sem Compromisso', '15 Minutos']
    },
    privacyText: '🔒 Seus dados estão seguros. Não enviamos spam e você pode cancelar a qualquer momento.'
  },
  footer: {
    logoUrl: '/images/logo-site.png',
    tagline: 'Transformando atendimento em vendas com Inteligência Artificial.',
    copyright: 'XYZ Soluciona. Todos os direitos reservados.'
  }
}
</script>

<template>
  <div class="min-h-screen bg-black text-white font-sans">
    <Header :logo-url="pageData.header.logoUrl" :nav-links="pageData.header.navLinks" />
    <HeroSection v-bind="pageData.hero" />
    <ProblemSection v-bind="pageData.problem" />
    <SolutionSection v-bind="pageData.solution" />
    <RoiSection v-bind="pageData.roi" />
    <GrowthCtaSection v-bind="pageData.growthCta" />
    <TestimonialSection v-bind="pageData.testimonial" />
    <FinalCtaSection v-bind="pageData.finalCta" />
    <Footer v-bind="pageData.footer" />
  </div>
</template>

<style>
body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  background-color: #000;
}
</style>
