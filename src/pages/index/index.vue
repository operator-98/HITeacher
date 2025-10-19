<template>
  <view class="home-page">
    <HeroSection />
    <!-- 删除了 <GenomicsCourseBanner /> -->
    <MutationsSection />
    <HeightSection />
    <KnowledgeSection />
    <FooterSection />
  </view>
</template>

<script setup lang="ts">
import HeroSection from '@/components/HeroSection.vue';
// 删除了 import GenomicsCourseBanner from '@/components/GenomicsCourseBanner.vue';
import MutationsSection from '@/components/MutationsSection.vue';
import HeightSection from '@/components/HeightSection.vue';
import KnowledgeSection from '@/components/KnowledgeSection.vue';
import FooterSection from '@/components/FooterSection.vue';
</script>

<style>
page {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', 'PingFang SC', 'Hiragino Sans GB', 'Microsoft YaHei', 'Helvetica Neue', sans-serif;
  line-height: 1.6;
  background-color: #ffffff;
  color: #333;
  margin: 0;
  padding: 0;
}
</style>