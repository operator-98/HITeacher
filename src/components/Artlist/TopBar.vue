<template>
  <view class="topbar">
    <view class="search-bar">
      <text class="search-icon">🔍</text>
      <input class="search-input" type="text" placeholder="Search" />
      <text class="filter-icon">→</text>
    </view>

    <view class="nav-actions">
      <!-- 删除了 subscribe-btn 按钮 -->
      <!-- <button class="subscribe-btn">Subscribe Now</button> -->
      <text class="nav-link">Business</text>
      <text class="nav-link">Pricing</text>
      <view class="avatar">B</view>
    </view>
  </view>
</template>

<script setup lang="ts"></script>

<style scoped>
.topbar {
  width: 100%;
  height: 70px;
  background-color: #F5F5F4; /* 使用项目主色调 */
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 24px;
  box-sizing: border-box;
  flex-shrink: 0;
}

.search-bar {
  display: flex;
  align-items: center;
  background-color: #E5E7EB; /* 使用浅灰色搜索框背景 */
  border-radius: 20px;
  padding: 8px 15px;
  width: 100%;
  max-width: 350px;
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

.filter-icon {
  font-size: 16px;
  color: #6B7280; /* 使用中灰色图标 */
  cursor: pointer;
}

.nav-actions {
  display: flex;
  align-items: center;
  gap: 20px;
}

/* 删除了 .subscribe-btn 样式 */

.nav-link {
  font-size: 14px;
  font-weight: 500;
  color: #333; /* 使用默认文字色 */
  cursor: pointer;
}
.nav-link:hover {
  color: #1E3A8A; /* 使用项目主色（靛蓝）悬停 */
}

.avatar {
  width: 32px;
  height: 32px;
  border-radius: 50%;
  background-color: #D1D5DB; /* 使用浅灰色头像背景 */
  color: #333; /* 使用深色文字 */
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  cursor: pointer;
}
</style>