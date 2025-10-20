<template>
  <view class="content-wrapper">
    <view class="header-section">
      <!-- 修改：将标题和搜索/上传栏放在同一行 -->
      <view class="title-and-search">
        <view class="title-wrapper">
          <view class="main-title"
            >探索 <text class="highlight-text">学习资源</text> 社区</view
          >
          <view class="subtitle"
            >从课程笔记、习题解析到小组讨论，总有你需要的。</view
          >
        </view>

        <view class="search-and-upload">
          <button class="upload-button">上传资源</button>
          <view class="search-bar">
            <text class="search-icon">🔍</text>
            <input class="search-input" type="text" placeholder="搜索学习资源..." />
            <button class="search-button">搜索</button>
          </view>
        </view>
      </view>
      <!-- 新增：分割线 -->
      <view class="divider"></view>
    </view>

    <!-- 资源列表部分 -->
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
/* --- 新增：分割线样式 --- */
.divider {
  height: 1px;
  background-color: #D1D5DB; /* 使用浅灰色作为分割线 */
  margin: 10px 0; /* 上下留点间距 */
  width: 100%; /* 占满宽度 */
}

/* --- 标题和搜索上传栏的容器样式 --- */
.title-and-search {
  display: flex;
  justify-content: space-between; /* 标题部分和搜索上传部分分别靠左靠右 */
  align-items: flex-start; /* 顶部对齐 */
  gap: 20px; /* 中间留点间距 */
  /* margin-bottom: 20px; /1* 移除：这个间距不应该影响 header-section 的 padding *1/ */
}

.title-wrapper {
  flex: 1; /* 标题部分占据剩余空间 */
  /* 添加一些基础样式，确保内容稳定 */
  display: flex;
  flex-direction: column;
  min-width: 0; /* 防止 flex item 溢出 */
}

.search-and-upload {
  display: flex;
  align-items: flex-start; /* 与标题顶部对齐 */
  gap: 10px; /* 按钮和搜索栏之间留点间距 */
  flex-shrink: 0; /* 防止搜索栏和按钮被压缩 */
  /* 添加一些基础样式，确保内容稳定 */
  display: flex;
  align-items: center; /* 为了让按钮和搜索栏垂直居中对齐，如果需要的话 */
  /* 或者保持 flex-start 以对齐顶部 */
}

/* --- 搜索栏和按钮样式 (复用之前的样式) --- */
.upload-button {
  background-color: #B91C1C; /* 使用 Logo 中 "HI" 的深红色 */
  color: white;
  border: none;
  border-radius: 20px; /* 圆角按钮 */
  /* padding: 6px 16px; /1* 修改：调整垂直内边距以匹配搜索栏高度 *1/ */
  padding: 7px 16px; /* 修改：进一步调整，使其视觉高度与搜索栏更匹配 */
  font-size: 14px;
  font-weight: bold;
  cursor: pointer;
  /* uni-app button 样式重置 */
  margin: 0;
  line-height: normal;
  flex-shrink: 0; /* 防止按钮被压缩 */
}
/* #ifdef H5 */
.upload-button:after {
  border: none;
}
/* #endif */

.search-bar {
  display: flex;
  align-items: center;
  background-color: #E5E7EB; /* 使用与 sidebar 和 card 相似的浅灰色背景 */
  border-radius: 20px;
  padding: 8px 15px; /* 原始搜索栏高度 */
  max-width: 350px; /* 限制最大宽度 */
  flex-shrink: 0; /* 防止搜索栏被压缩 */
}
.search-icon {
  font-size: 16px;
  margin-right: 10px;
  color: #6B7280; /* 使用中灰色图标 */
}
.search-input {
  flex-grow: 1;
  background: transparent;
  border: none;
  color: #333; /* 使用默认文字色 */
  font-size: 14px;
}
/* H5 平台隐藏 input 默认样式 */
/* #ifdef H5 */
.search-input ::-webkit-input-placeholder {
  color: #9CA3AF; /* 使用浅灰色占位符 */
}
.search-input {
  outline: none;
}
/* #endif */

.search-button {
  background-color: #1E3A8A; /* 使用项目主色（靛蓝） */
  color: white;
  border: none;
  border-radius: 15px; /* 圆角按钮 */
  padding: 6px 12px;
  font-size: 14px;
  font-weight: bold;
  margin-left: 8px; /* 与输入框留出间距 */
  cursor: pointer;
  /* uni-app button 样式重置 */
  margin: 0;
  line-height: normal;
}
/* #ifdef H5 */
.search-button:after {
  border: none;
}
/* #endif */


/* --- 原有样式调整：移除之前添加的 top-search-bar 样式 --- */
.content-wrapper {
  /* padding: 0; /1* 移除 content-wrapper 的 padding，由内部元素提供 *1/ */
  /* background-color: #F5F5F4; /1* 使用项目主色调 *1/ */
  /* color: #333; /1* 使用项目默认文字色 *1/ */
  /* 增加最小高度，确保内容能撑满 */
  /* min-height: 100vh; */
  /* box-sizing: border-box; */
  /* display: flex; /1* 使用 flex 布局 *1/ */
  /* flex-direction: column; /1* 垂直排列 header 和 server-section *1/ */
  /* flex-grow: 1; /1* 让内容区域占据剩余空间 *1/ */
  /* 移除这些，因为滚动逻辑已移至父级 .main-content */
}

/* 1. 顶部标题 */
.header-section {
  /* padding: 40px 24px 0 24px; /1* 调整上内边距 *1/ */
  padding: 24px 24px 0 24px; /* 修改：调整顶部内边距，提供更多空间，同时保持左右内边距 */
  margin-left: 10px;
  /* background-color: #F5F5F4; /1* 确保背景色与项目一致 *1/ */
  /* display: flex; /1* 使用 flex 布局 *1/ */
  /* flex-direction: column; /1* 垂直排列 title-and-search 和 divider *1/ */
  /* align-items: stretch; /1* 拉伸子元素 *1/ */
  /* flex-shrink: 0; /1* 防止 header-section 被压缩 *1/ */
  /* 移除这些，因为 .main-content 负责布局和滚动 */
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
  /* margin-top: 20px; /1* 与 header-section 保持间距 *1/ */
  /* padding: 0 24px; /1* 添加左右内边距，与 header-section 对齐 *1/ */
  padding: 20px 24px; /* 为资源列表区域添加内边距 */
  flex-grow: 1; /* 占据剩余空间 */
  overflow-y: auto; /* 如果内容过多，允许滚动 */
}
.section-title {
  font-size: 20px;
  font-weight: 700;
  margin-bottom: 20px;
  /* margin-left: 10px; /1* 可选：如果不需要左边距 *1/ */
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