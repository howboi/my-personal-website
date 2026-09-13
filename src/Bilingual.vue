<script setup>
import { computed } from 'vue'
import { translations } from './bilingual'
const props = defineProps({ text: { type: String, required: true } })
const english = computed(() => translations[props.text])
</script>
<template><span class="bilingual"><span :lang="english ? 'zh-Hant' : 'en'">{{ text }}</span><span v-if="english" lang="en" class="translation">{{ english }}</span></span></template>
