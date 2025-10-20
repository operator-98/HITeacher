<template>
  <view class="artlist-home">
    <!-- 侧边栏组件，在移动端会隐藏导航项，但保留 Logo -->
    <SideBar class="sidebar-component" />

    <view class="main-area">
      <!-- 顶部栏组件 - 已删除 -->
      <!-- <TopBar class="topbar-component" /> -->
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
}

.sidebar-component {
  flex-shrink: 0;
  width: 240px; /* 侧边栏固定宽度 */
  height: 100vh; /* 保证侧边栏高度 */
  background-color: #E5E7EB; /* 与 SideBar.vue 样式一致 */
  padding: 20px;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  color: #6B7280; /* 与 SideBar.vue 样式一致 */
}

.main-area {
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  width: calc(100% - 240px); /* 占据剩余宽度 */
  padding: 20px; /* 为内容添加内边距 */
}

.content-component {
  flex-grow: 1; /* 占据剩余高度并允许滚动 */
  overflow-y: auto;
}

/* 移动端适配：侧边栏宽度调整，主区域占满 */
@media (max-width: 768px) {
  .artlist-home {
    flex-direction: column; /* 主容器改为垂直布局 */
  }
  .sidebar-component {
    width: 100%; /* 侧边栏占满全宽 */
    height: auto; /* 高度自适应 */
    /* display: block; */ /* 确保侧边栏显示 */
    padding: 10px 20px; /* 调整移动端内边距 */
  }
  .main-area {
    width: 100%; /* 主区域占满全宽 */
    height: auto; /* 高度自适应 */
    padding: 10px; /* 移动端减少内边距 */
  }
  /* .topbar-component { display: none; } */ /* TopBar 已删除 */
  .content-component {
    margin-top: 10px; /* 与 Logo 之间留点空间 */
  }
}
</style>