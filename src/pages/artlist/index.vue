<template>
  <view class="artlist-home">
    <!-- 侧边栏组件 - 改为固定定位 -->
    <view class="sidebar-fixed-container">
      <SideBar class="sidebar-component" />
    </view>

    <view class="main-area">
      <!-- 主内容组件 -->
      <MainContent class="content-component" />
    </view>
  </view>
</template>

<script setup lang="ts">
import SideBar from '@/components/Artlist/SideBar.vue';
// import TopBar from '@/components/Artlist/TopBar.vue'; // 已删除 import
import MainContent from '@/components/Artlist/MainContent.vue';
</script>

<style scoped>
.artlist-home {
  display: flex;
  width: 100%;
  min-height: 100vh;
  background-color: #F5F5F4; /* 使用项目主色调 */
  color: #333;              /* 使用项目默认文字色 */
  /* 移除 SideBar 的 flex-shrink 和 width，因为现在是 fixed */
  /* padding: 20px; */ /* 不在容器上加 padding，由内部组件处理 */
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
  /* 移除 flex-shrink: 0; 和 width/height */
  /* height: 100vh; */ /* fixed 定位后，高度由容器控制 */
  /* width: 240px; */ /* fixed 定位后，宽度由容器控制 */
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

.main-area {
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  /* width: calc(100% - 240px); */ /* 移除，因为 SideBar 是 fixed */
  padding: 20px; /* 为内容添加内边距 */
  padding-left: 260px; /* 关键：为固定的 SideBar (240px) 留出空间，并加上一点间距 (20px) */
  margin-left: 0; /* 确保 margin 不会覆盖 fixed 元素 */
  box-sizing: border-box;
}

.content-component {
  flex-grow: 1; /* 占据剩余高度并允许滚动 */
  overflow-y: auto;
}

/* 移动端适配：隐藏固定侧边栏，主区域占满 */
@media (max-width: 768px) {
  .sidebar-fixed-container {
    display: none; /* 隐藏固定定位的侧边栏容器 */
  }
  .main-area {
    padding-left: 20px; /* 移动端移除为侧边栏预留的左边距 */
  }
}
</style>