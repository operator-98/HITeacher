<template>
  <view class="sidebar">
    <!-- Logo 永远显示 -->
    <view class="logo">
      <text class="logo-hi">HI</text>
      <text class="logo-teacher">Teacher</text>
    </view>

    <!-- 导航列表，在移动端隐藏 -->
    <view class="nav-list">
      <view class="nav-item active"> <!-- 假设主页是当前激活项 -->
        <!-- <text class="icon">[H]</text> -->
        <text>主页</text>
      </view>
      <view class="nav-item">
        <!-- <text class="icon">[R]</text> -->
        <text>学习资源</text>
      </view>
      <view class="nav-item">
        <!-- <text class="icon">[P]</text> -->
        <text>优秀伙伴</text>
      </view>
      <view class="nav-item">
        <!-- <text class="icon">[S]</text> -->
        <text>学习小组</text>
      </view>
    </view>

    <!-- 删除了原来的用户列表 (user-list) -->
  </view>
</template>

<script setup lang="ts">
// TODO: 添加图标 (可以使用 uni-icons 或 SVG) 和路由逻辑
</script>

<style scoped>
.sidebar {
  width: 100%;
  /* height: 100vh; */ /* 移动端时可能不需要占满视口高度 */
  background-color: #E5E7EB; /* 使用浅灰色背景 (与 MainContent 保持一致) */
  padding: 20px;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  color: #6B7280; /* 使用中灰色文字 */
}

.logo {
  font-size: 28px;
  font-weight: bold;
  color: #1E3A8A; /* 使用靛蓝色整体，子元素再分别设置 */
  margin-bottom: 30px; /* 桌面端时的下边距 */
  padding-left: 10px;
  display: flex; /* 使 HI 和 Teacher 并排 */
  align-items: center; /* 垂直居中对齐 */
}

.logo-hi {
  color: #B91C1C; /* 使用深红色 */
}

.logo-teacher {
  color: #1E3A8A; /* 使用靛蓝色 */
}

.nav-list {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

/* 删除了 .user-list 样式 */

.nav-item {
  display: flex;
  align-items: center;
  /* gap: 12px; */ /* 修改：移除图标后的间距 */
  padding: 10px 10px;
  border-radius: 8px;
  font-size: 15px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s;
}

.nav-item:hover {
  background-color: #D1D5DB; /* 使用浅灰色悬停背景 */
  color: #1f2937; /* 使用深灰色悬停文字 */
}

.nav-item.active {
  background-color: #D1D5DB; /* 使用浅灰色激活背景 */
  color: #1f2937; /* 使用深灰色激活文字 */
}

/* 删除了 .icon 样式 */

/* 移动端适配：隐藏导航列表，调整 Logo 间距 */
@media (max-width: 768px) {
  .nav-list {
    display: none; /* 隐藏导航按钮列表 */
  }
  .logo {
    margin-bottom: 10px; /* 调整移动端 Logo 下边距，因为没有导航项了 */
    padding-left: 0; /* 调整移动端 Logo 左侧内边距 */
  }
}
</style>