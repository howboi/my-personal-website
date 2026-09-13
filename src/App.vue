<script setup>
import { ref } from 'vue'
import Bilingual from './Bilingual.vue'
import { biography } from './bilingual'
const menuOpen = ref(false)
const selected = ref(null)
const profile = { name: '潘永澔', role: 'Developer & Student', intro: '資訊與財金背景的研究生，專注探索 Web3、區塊鏈與 AI Agent，透過專題與黑客松累積實作經驗。', email: 'howard0427666@gmail.com', phone: '+886 958701491', github: 'https://github.com/howboi', linkedin: 'https://www.linkedin.com/in/%E6%B0%B8%E6%BE%94-%E6%BD%98-a6847b3b4/' }
const projects = [
  { title: '台股基本面估價與互動式 K 線分析。', name: 'ValuAI', cover: ['Valu', 'AI'], type: '金融資料應用', tags: ['Vue 3', 'FastAPI'], color: 'lavender', number: '01', url: 'https://github.com/howboi/ValuAI', description: '結合基本面估價與技術面分析的台股儀表板，支援上市、上櫃股票代碼與中文名稱搜尋。以 DCF、P/E 模型整合合理價，搭配安全邊際、支撐壓力位與互動式 K 線圖，整理研究所需的資訊。', details: ['Vue 3、Tailwind CSS 與 Lightweight Charts 呈現分析介面。', 'FastAPI 搭配 yfinance、Pandas 與 NumPy 處理資料與估價計算。'], note: '研究與作品展示用途，不構成投資建議。' },
  { title: '畢業專題・負責前端開發。', name: 'ProfiqAI', cover: ['Profiq', 'AI'], type: '畢業專題', tags: ['前端開發', 'Vue 3'], color: 'green', number: '02', url: 'https://github.com/Ynn622/ProfiqAI', description: '我在 ProfiqAI 專案中負責前端開發。', details: [] },
  { title: '負責前端開發。', name: 'GasPass', cover: ['Gas', 'Pass'], type: '前端專案', tags: ['前端開發'], color: 'lavender', number: '03', url: 'https://github.com/qwe638853/GasPass', description: '我在 GasPass 專案中負責前端開發。', details: [] }
]
const nav = [{ id: 'about', label: '關於我' }, { id: 'work', label: '精選作品' }, { id: 'contact', label: '聯絡我' }]
</script>

<template>
  <div>
    <header class="border-b border-black/10">
      <nav class="page-wrap flex min-h-24 items-center justify-between" aria-label="主要導覽 / Main navigation">
        <a href="#home" class="brand">YP<span class="text-lime-600">.</span></a>
        <div class="hidden items-center gap-10 md:flex"><a v-for="item in nav" :key="item.id" :href="`#${item.id}`" class="nav-link"><Bilingual :text="item.label" /></a><span class="nav-note">PERSONAL PROFILE / 2026</span></div>
        <button class="rounded-full border border-black/20 px-4 py-2 md:hidden" @click="menuOpen = !menuOpen" :aria-expanded="menuOpen" aria-controls="mobile-menu"><Bilingual :text="menuOpen ? '關閉' : '選單'" /></button>
      </nav>
      <div v-if="menuOpen" id="mobile-menu" class="page-wrap flex flex-col gap-5 pb-6 md:hidden"><a v-for="item in nav" :key="item.id" :href="`#${item.id}`" @click="menuOpen = false"><Bilingual :text="item.label" /></a></div>
    </header>

    <main id="home">
      <section class="page-wrap hero grid items-center gap-14 lg:grid-cols-[1.35fr_1fr]">
        <div>
          <p class="eyebrow mb-7">你好，我是 {{ profile.name }}<span class="translation" lang="en">HELLO, WORLD. I’M PAN, YUNG-HAO.</span></p>
          <h1>保持好奇，<br>讓想法<span class="relative inline-block">成真<svg class="underline-mark" viewBox="0 0 240 16" aria-hidden="true"><path d="M3 11Q115 -2 236 8"/></svg></span>。<span class="hero-translation" lang="en">Stay curious.<br>Bring ideas to life.</span></h1>
          <p class="mt-8 text-lg font-medium">{{ profile.role }}</p>
          <p class="mt-4 max-w-lg leading-8 text-stone-600"><Bilingual :text="profile.intro" /></p>
          <div class="mt-9 flex flex-wrap items-center gap-6"><a href="#work" class="button-primary"><Bilingual text="看看我的作品" /> <span aria-hidden="true">↗</span></a><a href="#about" class="text-sm underline decoration-stone-400 underline-offset-8"><Bilingual text="多認識我一點" /></a></div>
        </div>
        <figure class="portrait-card">
          <img src="/pan-yung-hao.jpg" alt="潘永澔坐在窗邊的生活照 / Pan Yung-Hao sitting by a window" width="1108" height="1477" fetchpriority="high" class="portrait-photo" />
          <figcaption class="portrait-caption"><p class="text-xl font-semibold">PAN, YUNG-HAO</p><p class="mt-2 text-sm text-white/75">Developer & Student</p></figcaption>
        </figure>
      </section>

      <section id="about" class="page-wrap section-block grid gap-10 md:grid-cols-[.7fr_1.3fr]">
        <div><p class="eyebrow">01 / ABOUT ME</p><h2 class="mt-4"><Bilingual text="不只是一段自我介紹。" /></h2></div>
        <div>
          <p class="about-lead"><Bilingual text="在資訊與區塊鏈之間，持續探索與實作。" /></p>
          <div class="mt-6 max-w-2xl space-y-7 leading-8 text-stone-600"><p v-for="paragraph in biography" :key="paragraph"><Bilingual :text="paragraph" /></p></div>
          <div class="mt-8 flex flex-wrap gap-3"><span v-for="skill in ['Python', 'Solidity', 'Web3 / DeFi', 'AI Agent', '區塊鏈黑客松', '團隊協作']" :key="skill" class="skill-tag"><Bilingual :text="skill" /></span></div>
        </div>
      </section>

      <section id="work" class="page-wrap section-block">
        <div class="mb-10 flex flex-wrap items-end justify-between gap-5"><div><p class="eyebrow">02 / SELECTED WORK</p><h2 class="mt-4"><Bilingual text="一些想法，一些實踐。" /></h2></div><span class="text-sm text-stone-500"><Bilingual text="公開專案 / GitHub" /></span></div>
        <div class="grid gap-8 md:grid-cols-2"><button v-for="project in projects" :key="project.number" class="project-card group text-left" @click="selected = project; $nextTick(() => $refs.detail.showModal())">
          <div class="project-cover" :class="project.color"><div class="flex justify-between text-xs tracking-widest"><span><Bilingual :text="project.type" /></span><span>PROJECT {{ project.number }}</span></div><p class="project-wordmark">{{ project.cover[0] }}<br><span>{{ project.cover[1] }}.</span></p><div class="flex items-center justify-between text-sm"><span><span v-for="tag in project.tags" :key="tag" class="mr-3 inline-block"><Bilingual :text="tag" /></span></span><span class="project-arrow" aria-hidden="true">↗</span></div></div>
          <div class="flex items-start justify-between gap-3 pt-5"><div><h3 class="text-xl font-semibold">{{ project.name }}</h3><p class="mt-2 text-sm text-stone-600"><Bilingual :text="project.title" /></p></div><span class="pt-1 text-xs text-stone-500">{{ project.number }}</span></div>
        </button></div>
      </section>

      <section id="contact" class="page-wrap pb-16"><div class="contact-panel"><p class="eyebrow">03 / GET IN TOUCH</p><div class="mt-6 flex flex-wrap items-end justify-between gap-8"><div><h2><Bilingual text="下一個好點子，或許從一句嗨開始。" /></h2><p class="mt-5 text-stone-600"><Bilingual text="聊聊合作、交流想法，或只是打聲招呼。" /></p></div><a v-if="profile.email" :href="`mailto:${profile.email}`" class="button-primary"><Bilingual text="寄信給我" /> ↗</a></div><div class="mt-10 grid gap-4 border-t border-black/10 pt-7 sm:grid-cols-2">
  <a :href="`mailto:${profile.email}`" class="contact-link"><span class="eyebrow text-stone-500">EMAIL</span><span class="break-all">{{ profile.email }}</span></a>
  <a href="tel:+886958701491" class="contact-link"><span class="eyebrow text-stone-500">PHONE</span><span>{{ profile.phone }}</span></a>
  <a :href="profile.github" target="_blank" rel="noopener noreferrer" class="contact-link"><span class="eyebrow text-stone-500">GITHUB</span><span>howboi ↗</span></a>
  <a :href="profile.linkedin" target="_blank" rel="noopener noreferrer" class="contact-link"><span class="eyebrow text-stone-500">LINKEDIN</span><span><Bilingual text="潘永澔" /></span></a>
</div></div></section>
    </main>
    <footer class="page-wrap flex flex-wrap justify-between gap-4 border-t border-black/10 py-7 text-xs text-stone-500"><span>© 2026 {{ profile.name }} · 個人網站<span lang="en" class="translation">© 2026 PAN, YUNG-HAO · Personal website</span></span><a href="#home"><Bilingual text="回到頂端" /> ↑</a></footer>
    <dialog ref="detail" class="project-dialog" @click="e => { if (e.target === $refs.detail) $refs.detail.close() }" @close="selected = null"><template v-if="selected"><div class="flex items-center justify-between gap-6"><p class="eyebrow">PROJECT {{ selected.number }} / <Bilingual :text="selected.type" /></p><button @click="$refs.detail.close()" class="rounded-full border border-black/20 px-4 py-2" autofocus aria-label="關閉作品介紹 / Close project details"><Bilingual text="關閉" /> ×</button></div><h2 class="mt-8">{{ selected.name }}</h2><p class="mt-6 leading-8 text-stone-600"><Bilingual :text="selected.description" /></p><ul v-if="selected.details.length" class="mt-5 list-disc space-y-2 pl-5 leading-7 text-stone-600"><li v-for="detail in selected.details" :key="detail"><Bilingual :text="detail" /></li></ul><p v-if="selected.note" class="mt-4 text-sm text-stone-500"><Bilingual :text="selected.note" /></p><a :href="selected.url" target="_blank" rel="noopener noreferrer" class="button-primary mt-7"><Bilingual text="在 GitHub 查看專案" /> ↗</a><div class="mt-8 flex flex-wrap gap-3"><span v-for="tag in selected.tags" :key="tag" class="skill-tag"><Bilingual :text="tag" /></span></div></template></dialog>
  </div>
</template>





