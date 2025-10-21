<!-- pages/profile/index.vue -->
<template>
  <view class="profile-page">
    <!-- 侧边栏 - 使用 fixed 定位 -->
    <view class="sidebar-fixed-container">
      <SideBar class="sidebar-component" />
    </view>

    <!-- 主内容区 - 包含 MainContent，负责滚动 -->
    <view class="main-content">
      <MainContent class="content-component" />
    </view>
  </view>
</template>

<script setup lang="ts">
import SideBar from '@/components/Artlist/SideBar.vue'; // 复用 Artlist 侧边栏
import MainContent from '@/components/Profile/MainContent.vue'; // <-- 使用新的内容组件
</script>

<style scoped>
.profile-page {
  display: flex;
  width: 100%;
  min-height: 100vh;
  background-color: #F5F5F4; /* 使用项目主色调 */
  color: #333;              /* 使用项目默认文字色 */
}

/* 新增：侧边栏固定定位容器 */
.sidebar-fixed-container {
  position: fixed;
  top: 0;
  left: 0;
  height: 100vh; /* 占满视口高度 */
  width: 240px; /* 与原 SideBar 宽度一致 */
  z-index: 100; /* 确保在主内容之上 */
  pointer-events: none; /* 确保不影响主内容区的点击 */
}

.sidebar-component {
  background-color: #E5E7EB; /* 与 SideBar.vue 样式一致 */
  padding: 20px;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  color: #6B7280; /* 与 SideBar.vue 样式一致 */
  height: 100%; /* 占满容器高度 */
  width: 100%; /* 占满容器宽度 */
  pointer-events: auto; /* 恢复侧边栏自身的点击事件 */
}

/* 修改：主内容区容器 */
.main-content {
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  /* width: calc(100% - 240px); /1* 移除，因为 SideBar 是 fixed *1/ */
  padding: 20px; /* 为内容添加内边距 */
  padding-left: 260px; /* 关键：为固定的 SideBar (240px) 留出空间，并加上一点间距 (20px) */
  margin-left: 0; /* 确保 margin 不会覆盖 fixed 元素 */
  box-sizing: border-box;
  min-height: 100vh; /* 确保至少占满视口高度 */
  overflow-y: auto; /* 关键：使此容器内部内容可滚动 */
}

.content-component {
  flex-grow: 1; /* 占据剩余高度 */
  /* display: flex; /1* 使用 flex 布局 *1/ */
  /* flex-direction: column; /1* 垂直排列 header 和 server-section *1/ */
  /* overflow-y: auto; /1* 移除：滚动由父容器 .main-content 处理 *1/ */
}

/* 移动端适配：隐藏固定侧边栏，主区域占满 */
@media (max-width: 768px) {
  .sidebar-fixed-container {
    display: none; /* 隐藏固定定位的侧边栏容器 */
  }
  .main-content {
    padding-left: 20px; /* 移动端移除为侧边栏预留的左边距 */
  }
}
</style>