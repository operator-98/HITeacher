<template>
  <view class="feed-wrapper">
    <!-- 主 Feed 流 -->
    <view class="main-feed">
      <view class="post-creator-wrapper">
        <view class="post-creator">
          <view class="avatar-placeholder small">[AV]</view>
          <view class="post-input-area">
            <!-- 修改：将提示文字改为“加入学习讨论” -->
            <view class="post-input">加入学习讨论</view>
            <view class="post-actions">
              <view class="action-icons">
                <!-- 修改：将 [img] 图标改为“图片”文字 -->
                <text class="icon">图片</text>
                <!-- <text class="icon">[gif]</text> -->
                <!-- <text class="icon">[poll]</text> -->
                <!-- <text class="icon">[emo]</text> -->
                <!-- <text class="icon">[sch]</text> -->
                <!-- <text class="icon">[loc]</text> -->
              </view>
              <button class="post-button">Post</button>
            </view>
          </view>
        </view>
      </view>

      <!-- 删除了 .show-posts-link 模块 -->
      <!-- <view class="show-posts-link"> Show 34 posts </view> -->

      <view class="tweet-card">
        <view class="avatar-placeholder">[AV]</view>
        <view class="tweet-content">
          <view class="tweet-header">
            <text class="user-name">Elon Musk</text>
            <!-- 删除 @handle -->
            <!-- <text class="user-handle">@elonmusk</text> -->
            <text class="dot">·</text>
            <text class="timestamp">Oct 19</text>
            <text class="dots-menu">...</text>
          </view>
          <view class="tweet-body">
            Logical consistency is essential to the sanity of AI
            <br />
            逻辑一致性对于人工智能的理智至关重要
          </view>
          <view class="tweet-actions">
            <!-- 修改：调整按钮顺序为 点赞、评论、转发，使用文字 -->
            <view class="action-item">
              <text>赞</text> <!-- 修改：使用文字 -->
              <text>6.1K</text> <!-- 可选：保留数量 -->
            </view>
            <view class="action-item">
              <text>评论</text> <!-- 修改：使用文字 -->
              <text>5.4K</text> <!-- 可选：保留数量 -->
            </view>
            <view class="action-item">
              <text>转发</text> <!-- 修改：使用文字 -->
              <text>61K</text> <!-- 可选：保留数量 -->
            </view>
          </view>
        </view>
      </view>

      <view class="tweet-card">
        <view class="avatar-placeholder">[AV]</view>
        <view class="tweet-content">
          <view class="tweet-header">
            <text class="user-name">NetSuite</text>
            <!-- 删除 @handle -->
            <!-- <text class="user-handle">@NetSuite</text> -->
            <text class="dot">·</text>
            <text class="ad-label">Ad</text>
            <text class="dots-menu">...</text>
          </view>
          <view class="tweet-body">
            Is your business using QuickBooks? Are you spending more time
            managing that than running your business? Upgrade to NetSuite today.
            <br />
            您的企业是否使用 QuickBooks？您是否花在管理它的时间比经营业务的时间更多？立即升级到 NetSuite。
          </view>
          <view class="ad-image-placeholder">
            [Upgrade From QuickBooks]
          </view>
          <view class="tweet-actions">
            <!-- 修改：调整按钮顺序为 点赞、评论、转发，使用文字 -->
            <view class="action-item">
              <text>赞</text> <!-- 修改：使用文字 -->
            </view>
            <view class="action-item">
              <text>评论</text> <!-- 修改：使用文字 -->
            </view>
            <view class="action-item">
              <text>转发</text> <!-- 修改：使用文字 -->
            </view>
          </view>
        </view>
      </view>
    </view>

    <!-- 右侧边栏 - 移出 feed-wrapper，使用 fixed 定位 -->
    <view class="right-sidebar-fixed">
      <view class="right-sidebar">
        <!-- 新增：搜索栏 -->
        <view class="search-bar">
          <text class="search-icon">🔍</text>
          <input class="search-input" type="text" placeholder="Search" />
          <!-- 新增：搜索按钮 -->
          <button class="search-button">Search</button>
        </view>

        <!-- 删除了 "Subscribe to Premium" 模块 -->
        <!-- <view class="sidebar-card"> -->
        <!--   <text class="card-title">Subscribe to Premium</text> -->
        <!--   <text class="card-body"> -->
        <!--     Subscribe to unlock new features and if eligible, receive a share of -->
        <!--     revenue. -->
        <!--   </text> -->
        <!--   <button class="subscribe-button">Subscribe</button> -->
        <!-- </view> -->

        <view class="sidebar-card">
          <view class="card-header">
            <text class="card-title">Today's News</text>
            <!-- 删除了 close-icon -->
            <!-- <text class="close-icon">✕</text> -->
          </view>
          <view class="news-list">
            <view class="news-item">
              <text class="news-title"
                >JD Vance Rallies Marines at Camp Pendleton Amid Shutdown and I-5
                Closur...</text
              >
              <text class="news-meta">2 days ago · News · 294.5K posts</text>
            </view>
            <view class="news-item">
              <text class="news-title"
                >Shutdown Blocks Swearing-In of Rep.-Elect Adelita Grijalva Over
                Epstein Files Dispute</text
              >
              <text class="news-meta">2 days ago · News · 74.2K posts</text>
            </view>
            <view class="news-item">
              <text class="news-title"
                >Streamer Emiru Assaulted at TwitchCon 2025 Over Security
                Lapses</text
              >
              <text class="news-meta"
                >2 days ago · Entertainment · 209.7K posts</text
              >
            </view>
          </view>
        </view>

        <view class="sidebar-card">
          <text class="card-title">What's happening</text>
          <view class="trend-item">
            <view class="trend-content">
              <text class="trend-category">Rushmore</text>
              <text class="trend-name">LIVE</text>
            </view>
            <view class="trend-image-placeholder">[Img]</view>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
// 该组件目前不需要脚本
</script>

<style scoped>
/* 主 Feed 流包装器 */
.feed-wrapper {
  width: 100%;
  display: flex;
  justify-content: center; /* 保持居中，但配合 max-width 可实现内容居中 */
  padding: 0 20px;
  box-sizing: border-box;
  background-color: #F5F5F4; /* 与项目主色调一致 */
  color: #333; /* 与项目主文字色一致 */
  min-height: 100vh; /* 确保容器至少占满视口高度 */
  /* 关键：为固定定位的右侧边栏留出空间 */
  padding-right: 370px; /* 侧边栏宽度 (350px) + 一些间距 (20px) */
}

/* 1. 主 Feed 流 */
.main-feed {
  width: 100%;
  max-width: 600px; /* 限制主内容区最大宽度 */
  min-height: 100vh; /* 确保主内容区有足够高度用于滚动 */
  background-color: #F5F5F4; /* 与父容器背景色一致 */
  /* 移除边框 */
  margin: 0 auto; /* 关键：让内容在容器中水平居中 */
}

.avatar-placeholder {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background-color: #D1D5DB; /* 使用浅灰色背景 */
  color: #6B7280; /* 使用中灰色文字 */
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  font-size: 12px;
}
.avatar-placeholder.small {
  width: 40px;
  height: 40px;
}

/* 1.1 Post Creator - 修改：添加卡片背景色 */
.post-creator-wrapper {
  /* padding: 10px 15px; */ /* 移除或调整内边距 */
  /* border-bottom: 1px solid #D1D5DB; */ /* 移除边框 */
  background-color: #E5E7EB; /* 使用与 sidebar-card 一致的背景色 */
  border-radius: 12px; /* 添加圆角 */
  margin: 15px; /* 添加外边距 */
  padding: 10px 15px; /* 保留内边距 */
}
.post-creator {
  display: flex;
  gap: 12px;
}
.post-input-area {
  width: 100%;
}
.post-input {
  font-size: 20px;
  padding: 12px 0;
  color: #9CA3AF; /* 使用浅灰色提示文字 */
}
.post-actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 12px;
  /* border-top: 1px solid #D1D5DB; */ /* 移除边框 */
}
.action-icons {
  display: flex;
  gap: 15px;
  color: #1E3A8A; /* 使用项目主色（靛蓝） */
}
.icon {
  font-size: 14px;
  cursor: pointer;
}
.post-button {
  background-color: #1E3A8A; /* 使用项目主色（靛蓝） */
  color: white;
  border: none;
  border-radius: 20px;
  padding: 8px 16px;
  font-size: 15px;
  font-weight: bold;
  cursor: pointer;
  opacity: 0.8;
  /* uni-app button 样式重置 */
  margin: 0;
  line-height: normal;
}
/* #ifdef H5 */
.post-button:after {
  border: none;
}
/* #endif */

/* 1.2 Show Posts - 已删除 */
/* .show-posts-link { ... } */

/* 1.3 Tweet Card */
.tweet-card {
  display: flex;
  gap: 12px;
  padding: 15px;
  border-bottom: 1px solid #D1D5DB; /* 使用浅灰色边框 */
}
.tweet-content {
  width: 100%;
}
.tweet-header {
  display: flex;
  align-items: center;
  gap: 5px;
  font-size: 15px;
  margin-bottom: 4px;
}
.user-name {
  font-weight: bold;
  color: #1f2937; /* 使用深灰色文字 */
}
/* .user-handle, */ /* 已删除 */
.dot,
.timestamp {
  color: #6B7280; /* 使用中灰色文字 */
}
.ad-label {
  color: #6B7280; /* 使用中灰色文字 */
  font-size: 13px;
  font-weight: bold;
}
.dots-menu {
  margin-left: auto;
  color: #6B7280; /* 使用中灰色文字 */
  font-weight: bold;
  cursor: pointer;
}
.tweet-body {
  font-size: 15px;
  line-height: 1.5;
  margin-bottom: 12px;
}
.ad-image-placeholder {
  width: 100%;
  height: 280px;
  border-radius: 12px;
  background-color: #E5E7EB; /* 使用浅灰色背景 */
  border: 1px solid #D1D5DB; /* 使用浅灰色边框 */
  color: #9CA3AF; /* 使用浅灰色文字 */
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 12px;
}
.tweet-actions {
  display: flex;
  justify-content: space-between;
  color: #6B7280; /* 使用中灰色文字 */
  font-size: 13px;
}
.action-item {
  display: flex;
  align-items: center;
  gap: 5px;
  cursor: pointer;
}
.action-item:hover {
  color: #1E3A8A; /* 使用项目主色（靛蓝）悬停 */
}
/* .action-item .icon { */ /* 已删除图标样式 */
/*   font-size: 16px; */
/* } */
/* .actions-right { */
/*   flex-grow: 1; */
/*   justify-content: flex-end; */
/*   gap: 15px; */
/* } */

/* 2. 右侧边栏 - 固定定位容器 */
.right-sidebar-fixed {
  position: fixed;
  top: 0; /* 从视口顶部开始 */
  right: 0; /* 从视口右侧开始 */
  height: 100vh; /* 占满视口高度 */
  width: 350px; /* 与原侧边栏宽度一致 */
  display: flex;
  justify-content: flex-end; /* 让内部侧边栏靠右对齐 */
  pointer-events: none; /* 确保不影响主内容区的点击 */
  z-index: 100; /* 确保在主内容之上 */
}

.right-sidebar {
  width: 350px;
  flex-shrink: 0;
  padding-top: 10px;
  display: flex;
  flex-direction: column;
  gap: 15px;
  height: 100%; /* 占满父容器高度 */
  overflow-y: auto; /* 如果内容超出高度，允许滚动 */
  pointer-events: auto; /* 恢复侧边栏自身的点击事件 */
  /* 滚动条样式 (可选) */
  scrollbar-width: thin;
  scrollbar-color: #1E3A8A #E5E7EB;
  /* 背景色等样式 */
  background-color: #F5F5F4; /* 与主背景色一致，或使用卡片背景色 */
  padding-right: 20px; /* 与 .feed-wrapper 的 padding 保持一致 */
  box-sizing: border-box;
}
.right-sidebar::-webkit-scrollbar {
  width: 6px;
}
.right-sidebar::-webkit-scrollbar-track {
  background: #E5E7EB;
}
.right-sidebar::-webkit-scrollbar-thumb {
  background-color: #1E3A8A;
  border-radius: 3px;
}

/* 新增：搜索栏样式 */
.search-bar {
  display: flex;
  align-items: center;
  background-color: #E5E7EB; /* 使用浅灰色背景 */
  border-radius: 20px;
  padding: 8px 15px;
  margin-bottom: 10px; /* 与下方卡片留点间距 */
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

/* 新增：搜索按钮样式 */
.search-button {
  background-color: #1E3A8A; /* 使用项目主色（靛蓝） */
  color: white;
  border: none;
  border-radius: 20px;
  padding: 8px 16px;
  font-size: 15px;
  font-weight: bold;
  cursor: pointer;
  margin: 0;
  line-height: normal;
}
/* #ifdef H5 */
.search-button:after {
  border: none;
}
/* #endif */

.sidebar-card {
  background-color: #E5E7EB; /* 使用浅灰色背景 */
  border-radius: 12px;
  padding: 15px;
  color: #333; /* 使用默认文字色 */
  width: calc(350px - 40px); /* 减去 padding 和 margin，确保不超出容器 */
  box-sizing: border-box;
}

.card-title {
  font-size: 20px;
  font-weight: bold;
  color: #1f2937; /* 使用深灰色文字 */
  display: block;
}
.card-body {
  font-size: 15px;
  color: #333; /* 使用默认文字色 */
  line-height: 1.4;
  margin: 10px 0 15px;
}
/* .subscribe-button {
  background-color: #1E3A8A; /1* 使用项目主色（靛蓝） *1/
  color: white;
  border: none;
  border-radius: 20px;
  padding: 8px 16px;
  font-size: 15px;
  font-weight: bold;
  cursor: pointer;
  margin: 0;
  line-height: normal;
} */
/* #ifdef H5 */
/* .subscribe-button:after {
  border: none;
} */
/* #endif */

/* 2.2 News Card */
.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
}
/* .close-icon { */ /* 已删除 */
/*   color: #6B7280; /1* 使用中灰色文字 *1/ */
/*   font-size: 20px; */
/*   cursor: pointer; */
/* } */
.news-list {
  display: flex;
  flex-direction: column;
  gap: 15px;
}
.news-item {
  cursor: pointer;
}
.news-title {
  font-size: 15px;
  font-weight: bold;
  color: #1f2937; /* 使用深灰色文字 */
  display: block;
}
.news-meta {
  font-size: 13px;
  color: #6B7280; /* 使用中灰色文字 */
}

/* 2.3 Trend Card */
.trend-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 15px;
  cursor: pointer;
}
.trend-content {
  display: flex;
  flex-direction: column;
}
.trend-category {
  font-size: 13px;
  color: #6B7280; /* 使用中灰色文字 */
}
.trend-name {
  font-size: 15px;
  font-weight: bold;
  color: #1f2937; /* 使用深灰色文字 */
}
.trend-image-placeholder {
  width: 60px;
  height: 60px;
  border-radius: 8px;
  background-color: #D1D5DB; /* 使用浅灰色背景 */
  color: #9CA3AF; /* 使用浅灰色文字 */
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 12px;
  flex-shrink: 0;
}

/* 移动端适配：隐藏右侧边栏 */
@media (max-width: 1000px) {
  .right-sidebar-fixed {
    display: none; /* 隐藏固定定位的侧边栏容器 */
  }
  .feed-wrapper {
    justify-content: flex-start; /* 移动端让内容左对齐 */
    padding: 0 10px; /* 减少移动端侧边内边距 */
    padding-right: 0; /* 移动端移除为侧边栏预留的右边距 */
  }
  .main-feed {
    max-width: 100%; /* 移动端主区域占满 */
  }
}
@media (max-width: 768px) {
  .feed-wrapper {
    padding: 0;
  }
  /* .main-feed { /1* 已在上面的媒体查询中处理 *1/
    /1* border-left: none; /1* 已移除 *1/
    /1* border-right: none; /1* 已移除 *1/
  /1* } */
}
</style>