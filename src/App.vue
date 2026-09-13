<script setup>
import { ref } from 'vue'
const menuOpen = ref(false)
const selected = ref(null)
const profile = { name: '潘永澔', role: 'Developer & Student', intro: '以資訊與財金為起點，探索程式、金融市場與區塊鏈的交會。熱衷學習，也樂於透過實作與合作，讓想法一步步成真。', email: 'howard0427666@gmail.com', phone: '+886 958701491', github: 'https://github.com/howboi', linkedin: 'https://www.linkedin.com/in/%E6%B0%B8%E6%BE%94-%E6%BD%98-a6847b3b4/' }
const projects = [
  { title: '台股基本面估價與互動式 K 線分析。', name: 'ValuAI', cover: ['Valu', 'AI'], type: '金融資料應用', tags: ['Vue 3', 'FastAPI'], color: 'lavender', number: '01', url: 'https://github.com/howboi/ValuAI', description: '結合基本面估價與技術面分析的台股儀表板，支援上市、上櫃股票代碼與中文名稱搜尋。以 DCF、P/E 模型整合合理價，搭配安全邊際、支撐壓力位與互動式 K 線圖，整理研究所需的資訊。', details: ['Vue 3、Tailwind CSS 與 Lightweight Charts 呈現分析介面。', 'FastAPI 搭配 yfinance、Pandas 與 NumPy 處理資料與估價計算。'], note: '研究與作品展示用途，不構成投資建議。' },
  { title: '以 Vue 3 與 Vite 建置的畢業專題前端。', name: '畢業專題前端', cover: ['Graduation', 'Project'], type: '前端專案', tags: ['Vue 3', 'Vite'], color: 'green', number: '02', url: 'https://github.com/howboi/graduation-project-frontend', description: '畢業專題的前端程式庫，使用 Vue 3 與 Vite 建立開發環境，採用單檔元件與 script setup 語法。專案 README 同時提供 Figma 設計稿連結。', details: ['以 Vue 單檔元件組織前端介面。', '可至 GitHub 查看原始碼與 README 中的設計參考。'] },
  { title: 'Solidity 智慧合約與 ERC-20 實作練習。', name: 'SolidityProjects', cover: ['Solidity', 'Projects'], type: '智慧合約練習', tags: ['Solidity', 'Hardhat'], color: 'lavender', number: '03', url: 'https://github.com/howboi/SolidityProjects', description: '以 Solidity 與 Hardhat 為基礎的智慧合約練習專案。程式庫收錄 ERC20.sol、IERC20.sol 與 Lock.sol 等合約檔案，以及 Hardhat 設定，呈現區塊鏈開發的學習與實作。', details: ['收錄 ERC-20 合約與介面實作檔案。', '使用 Hardhat 作為合約開發工具。'] }
]
const nav = [{ id: 'about', label: '關於我' }, { id: 'work', label: '精選作品' }, { id: 'contact', label: '聯絡我' }]
</script>

<template>
  <div>
    <header class="border-b border-black/10">
      <nav class="page-wrap flex min-h-24 items-center justify-between" aria-label="主要導覽">
        <a href="#home" class="brand">YP<span class="text-lime-600">.</span></a>
        <div class="hidden items-center gap-10 md:flex"><a v-for="item in nav" :key="item.id" :href="`#${item.id}`" class="nav-link">{{ item.label }}</a><span class="nav-note">PERSONAL PROFILE / 2026</span></div>
        <button class="rounded-full border border-black/20 px-4 py-2 md:hidden" @click="menuOpen = !menuOpen" :aria-expanded="menuOpen" aria-controls="mobile-menu">{{ menuOpen ? '關閉' : '選單' }}</button>
      </nav>
      <div v-if="menuOpen" id="mobile-menu" class="page-wrap flex flex-col gap-5 pb-6 md:hidden"><a v-for="item in nav" :key="item.id" :href="`#${item.id}`" @click="menuOpen = false">{{ item.label }}</a></div>
    </header>

    <main id="home">
      <section class="page-wrap hero grid items-center gap-14 lg:grid-cols-[1.35fr_1fr]">
        <div>
          <p class="eyebrow mb-7">HELLO, WORLD. 我是 {{ profile.name }}</p>
          <h1>保持好奇，<br>讓想法<span class="relative inline-block">成真<svg class="underline-mark" viewBox="0 0 240 16" aria-hidden="true"><path d="M3 11Q115 -2 236 8"/></svg></span>。</h1>
          <p class="mt-8 text-lg font-medium">{{ profile.role }}</p>
          <p class="mt-4 max-w-lg leading-8 text-stone-600">{{ profile.intro }}</p>
          <div class="mt-9 flex flex-wrap items-center gap-6"><a href="#work" class="button-primary">看看我的作品 <span aria-hidden="true">↗</span></a><a href="#about" class="text-sm underline decoration-stone-400 underline-offset-8">多認識我一點</a></div>
        </div>
        <figure class="portrait-card">
          <img src="/pan-yung-hao.jpg" alt="潘永澔坐在窗邊的生活照" width="1108" height="1477" fetchpriority="high" class="portrait-photo" />
          <figcaption class="portrait-caption"><p class="text-xl font-semibold">PAN, YUNG-HAO</p><p class="mt-2 text-sm text-white/75">Developer & Student</p></figcaption>
        </figure>
      </section>

      <section id="about" class="page-wrap section-block grid gap-10 md:grid-cols-[.7fr_1.3fr]">
        <div><p class="eyebrow">01 / ABOUT ME</p><h2 class="mt-4">不只是一段<br>自我介紹。</h2></div>
        <div>
          <p class="about-lead">在金融與科技之間，<br class="hidden md:block">保持好奇，持續實作。</p>
          <div class="mt-5 max-w-2xl space-y-5 leading-8 text-stone-600">
            <p>我畢業於國立臺北科技大學資訊與財金管理系，目前持續於該系所就讀。個性負責、重視效率，熱衷學習新知，也樂於與人合作。</p>
            <p>高中時受父親影響，開始接觸證券交易；進入大學後自行操作股票市場，持續研究個股並關注國際新聞。隨著系上推動區塊鏈相關領域，我也對加密貨幣產生濃厚興趣，投入研究與投資，探索金融與科技的更多可能。</p>
            <p>程式方面，我具備 Python 與 Solidity 智慧合約語言的基礎，並在課程與專題中累積實際應用經驗。大學期間多次籌辦校內活動，培養了溝通協調與組織能力，也學會在團隊合作中兼顧效率與責任。</p>
          </div>
          <div class="mt-8 flex flex-wrap gap-3"><span v-for="skill in ['Python', 'Solidity', '金融市場研究', '區塊鏈', '團隊協作', '活動籌辦']" :key="skill" class="skill-tag">{{ skill }}</span></div>
        </div>
      </section>

      <section id="work" class="page-wrap section-block">
        <div class="mb-10 flex flex-wrap items-end justify-between gap-5"><div><p class="eyebrow">02 / SELECTED WORK</p><h2 class="mt-4">一些想法，一些實踐。</h2></div><span class="text-sm text-stone-500">公開專案 / GitHub</span></div>
        <div class="grid gap-8 md:grid-cols-2"><button v-for="project in projects" :key="project.number" class="project-card group text-left" @click="selected = project; $nextTick(() => $refs.detail.showModal())">
          <div class="project-cover" :class="project.color"><div class="flex justify-between text-xs tracking-widest"><span>{{ project.type }}</span><span>PROJECT {{ project.number }}</span></div><p class="project-wordmark">{{ project.cover[0] }}<br><span>{{ project.cover[1] }}.</span></p><div class="flex items-center justify-between text-sm"><span>{{ project.tags.join(' / ') }}</span><span class="project-arrow" aria-hidden="true">↗</span></div></div>
          <div class="flex items-start justify-between gap-3 pt-5"><div><h3 class="text-xl font-semibold">{{ project.name }}</h3><p class="mt-2 text-sm text-stone-600">{{ project.title }}</p></div><span class="pt-1 text-xs text-stone-500">{{ project.number }}</span></div>
        </button></div>
      </section>

      <section id="contact" class="page-wrap pb-16"><div class="contact-panel"><p class="eyebrow">03 / GET IN TOUCH</p><div class="mt-6 flex flex-wrap items-end justify-between gap-8"><div><h2>下一個好點子，<br>或許從一句嗨開始。</h2><p class="mt-5 text-stone-600">聊聊合作、交流想法，或只是打聲招呼。</p></div><a v-if="profile.email" :href="`mailto:${profile.email}`" class="button-primary">寄信給我 ↗</a><span v-else class="rounded-full border border-black/20 px-6 py-4 text-sm">聯絡信箱待補上</span></div><div class="mt-10 grid gap-4 border-t border-black/10 pt-7 sm:grid-cols-2">
  <a :href="`mailto:${profile.email}`" class="contact-link"><span class="eyebrow text-stone-500">EMAIL</span><span class="break-all">{{ profile.email }}</span></a>
  <a href="tel:+886958701491" class="contact-link"><span class="eyebrow text-stone-500">PHONE</span><span>{{ profile.phone }}</span></a>
  <a :href="profile.github" target="_blank" rel="noopener noreferrer" class="contact-link"><span class="eyebrow text-stone-500">GITHUB</span><span>howboi ↗</span></a>
  <a :href="profile.linkedin" target="_blank" rel="noopener noreferrer" class="contact-link"><span class="eyebrow text-stone-500">LINKEDIN</span><span>潘永澔 · PAN, YUNG-HAO ↗</span></a>
</div></div></section>
    </main>
    <footer class="page-wrap flex flex-wrap justify-between gap-4 border-t border-black/10 py-7 text-xs text-stone-500"><span>© 2026 {{ profile.name }}. 個人網站初稿</span><a href="#home">回到頂端 ↑</a></footer>
    <dialog ref="detail" class="project-dialog" @click="e => { if (e.target === $refs.detail) $refs.detail.close() }" @close="selected = null"><template v-if="selected"><div class="flex items-center justify-between gap-6"><p class="eyebrow">PROJECT {{ selected.number }} / {{ selected.type }}</p><button @click="$refs.detail.close()" class="rounded-full border border-black/20 px-4 py-2" autofocus aria-label="關閉作品介紹">關閉 ×</button></div><h2 class="mt-8">{{ selected.name }}</h2><p class="mt-6 leading-8 text-stone-600">{{ selected.description }}</p><ul class="mt-5 list-disc space-y-2 pl-5 leading-7 text-stone-600"><li v-for="detail in selected.details" :key="detail">{{ detail }}</li></ul><p v-if="selected.note" class="mt-4 text-sm text-stone-500">{{ selected.note }}</p><a :href="selected.url" target="_blank" rel="noopener noreferrer" class="button-primary mt-7">在 GitHub 查看專案 ↗</a><div class="mt-8 flex flex-wrap gap-3"><span v-for="tag in selected.tags" :key="tag" class="skill-tag">{{ tag }}</span></div></template></dialog>
  </div>
</template>



