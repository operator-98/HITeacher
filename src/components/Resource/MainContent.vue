<template>
  <view class="content-wrapper">
    <view class="header-section">
      <!-- 修改：标题和副标题 -->
      <view class="main-title"
        >探索 <text class="highlight-text">学习资源</text> 社区</view
      >
      <view class="subtitle"
        >从课程笔记、习题解析到小组讨论，总有你需要的。</view
      >
    </view>

    <view class="server-section">
      <!-- 修改：标题 -->
      <view class="section-title">精选资源</view>

      <view class="server-grid">
        <view
          class="server-card"
          v-for="server in servers"
          :key="server.name"
        >
          <view class="card-banner-placeholder">
            [{{ server.name }} 资源封面]
          </view>
          
          <view class="card-icon-placeholder">[{{ server.initial }}]</view>
          
          <view class="card-content">
            <view class="card-title">
              <view class="online-dot"></view>
              <text>{{ server.name }}</text>
            </view>
            <view class="card-description">{{ server.description }}</view>
            <view class="card-stats">
              <text>• {{ server.online }} 人正在学习</text>
              <text>• {{ server.members }} 份资料</text>
            </view>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref } from 'vue';

interface Server {
  name: string;
  initial: string; // 用于图标占位符
  description: string;
  online: string;
  members: string;
}

const servers = ref<Server[]>([
  {
    name: '计算机科学导论',
    initial: 'CS',
    description:
      '涵盖编程基础、算法与数据结构等核心知识。',
    online: '745',
    members: '4,149',
  },
  {
    name: '高等数学',
    initial: 'GM',
    description:
      '微积分、线性代数、概率论等学习资料与习题解析。',
    online: '703',
    members: '20,312',
  },
  {
    name: '大学物理',
    initial: 'UP',
    description:
      '经典力学、电磁学、光学等课程笔记与实验报告。',
    online: '354',
    members: '2,164',
  },
  {
    name: '英语四级',
    initial: 'CET',
    description:
      '历年真题、词汇解析、听力练习等备考资源。',
    online: '299',
    members: '1,458',
  },
]);
</script>

<style scoped>
/* --- 移除 content-wrapper 的 padding 和背景色，由父页面提供 --- */
/* content-wrapper {
  padding: 24px;
  background-color: #F5F5F4; /1* 使用项目主色调 *1/
  color: #333; /1* 使用项目默认文字色 *1/
} */

/* 1. 顶部标题 */
.header-section {
  padding: 40px 0;
  margin-left: 10px;
}
.main-title {
  font-size: 32px;
  font-weight: 800;
  margin-bottom: 8px;
  color: #1f2937; /* 使用深灰色文字 */
}
.highlight-text {
  font-family: 'Arial Black', sans-serif; /* 模拟强调字体 */
  color: #1E3A8A; /* 使用项目主色（靛蓝） */
}
.subtitle {
  font-size: 16px;
  color: #6B7280; /* 使用中灰色文字 */
}

/* 2. 精选服务器 -> 精选资源 */
.server-section {
  margin-top: 20px;
}
.section-title {
  font-size: 20px;
  font-weight: 700;
  margin-bottom: 20px;
  margin-left: 10px;
  color: #1f2937; /* 使用深灰色文字 */
}

.server-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 20px;
}

.server-card {
  background-color: #E5E7EB; /* 使用浅灰色背景 */
  border-radius: 8px;
  overflow: hidden;
  cursor: pointer;
  transition: transform 0.2s, background-color 0.2s;
  position: relative;
}
.server-card:hover {
  transform: translateY(-5px);
  background-color: #D1D5DB; /* 使用更浅的灰色悬停背景 */
}

.card-banner-placeholder {
  width: 100%;
  height: 160px;
  background-color: #D1D5DB; /* 使用浅灰色背景 */
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px;
  color: #9CA3AF; /* 使用浅灰色文字 */
}

.card-icon-placeholder {
  width: 48px;
  height: 48px;
  border-radius: 12px;
  background-color: #1E3A8A; /* 使用项目主色（靛蓝） */
  border: 3px solid #F5F5F4; /* 使用项目主色调边框 */
  position: absolute;
  top: 136px; /* 160px (banner) - 24px (half icon) */
  left: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 12px;
  color: white;
  font-weight: bold;
}

.card-content {
  padding: 40px 16px 16px 16px; /* 顶部 padding 留出 icon 位置 */
}

.card-title {
  font-size: 18px;
  font-weight: 700;
  color: #1f2937; /* 使用深灰色文字 */
  margin-bottom: 8px;
  display: flex;
  align-items: center;
}

.online-dot {
  width: 8px;
  height: 8px;
  background-color: #10B981; /* 使用项目可能的强调色（绿色） */
  border-radius: 50%;
  margin-right: 8px;
}

.card-description {
  font-size: 14px;
  color: #6B7280; /* 使用中灰色文字 */
  line-height: 1.4;
  height: 60px; /* 限制高度，约 3-4 行 */
  overflow: hidden;
  text-overflow: ellipsis;
}

.card-stats {
  margin-top: 12px;
  font-size: 12px;
  color: #6B7280; /* 使用中灰色文字 */
  display: flex;
  gap: 12px;
}
</style>