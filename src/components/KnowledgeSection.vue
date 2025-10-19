<template>
  <view class="knowledge-wrapper">
    <text class="main-title">Passing down knowledge</text>
    <view class="divider"></view>

    <view class="profile-grid">
      <view
        class="profile-card"
        v-for="researcher in researchers"
        :key="researcher.name"
      >
        <view class="image-placeholder">{{ researcher.imagePlaceholder }}</view>
        <view class="profile-text">
          <text class="profile-name">{{ researcher.name }}</text>
          <text class="profile-desc">{{ researcher.description }}</text>
        </view>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref } from 'vue';

interface Researcher {
  name: string;
  description: string;
  imagePlaceholder: string;
}

const researchers = ref<Researcher[]>([
  {
    name: 'Feyisayo Eweje',
    description:
      "At Harvard's Wyss Institute, Feyisayo is working on a method to transport gene editors to the right cells in the body, so they can directly correct mutations.",
    imagePlaceholder: '[Feyisayo Eweje]',
  },
  {
    name: 'Christina Warinner',
    description:
      'As a professor of scientific archaeology, Christina uses ancient DNA in her pioneering work cracking the mysteries of early human diets and health.',
    imagePlaceholder: '[Christina Warinner]',
  },
  {
    name: 'Susan Kuo',
    description:
      'At Massachusetts General Hospital, Susan focuses on how genetic changes may shift over time for people with neuropsychiatric disabilities.',
    imagePlaceholder: '[Susan Kuo]',
  },
]);
</script>

<style scoped>
.knowledge-wrapper {
  max-width: 1200px;
  margin: 0 auto;
  padding: 60px 20px;
  box-sizing: border-box;
}

.main-title {
  font-size: 42px;
  font-weight: 300;
  display: block;
}

.divider {
  border-top: 1px solid #000;
  width: 100%;
  margin: 20px 0 40px;
}

.profile-grid {
  display: flex;
  justify-content: space-between;
  gap: 30px;
  flex-wrap: wrap; /* 移动端自动换行 */
}

.profile-card {
  flex: 1;
  min-width: 300px;
  max-width: calc(33.333% - 20px); /* 保持三列, 减去 gap */
  background-color: #f4f4f4;
  box-sizing: border-box;
}

.image-placeholder {
  width: 100%;
  height: 250px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #e0e0e0;
  color: #888;
  font-size: 16px;
}

.profile-text {
  padding: 25px;
}

.profile-name {
  font-size: 24px;
  font-weight: 500;
  display: block;
  margin-bottom: 10px;
}

.profile-desc {
  font-size: 16px;
  line-height: 1.6;
}

@media (max-width: 992px) {
  .profile-card {
    max-width: calc(50% - 15px); /* 中等屏幕两列 */
  }
}

@media (max-width: 768px) {
  .profile-card {
    max-width: 100%; /* 移动端一列 */
  }
}
</style>