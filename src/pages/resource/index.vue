<template>
  <view class="resource-page">
    <SideBar class="sidebar-component" />

    <view class="main-area">
      <MainContent class="content-component" />
    </view>
  </view>
</template>

<script setup lang="ts">
import SideBar from '@/components/Artlist/SideBar.vue'; // 复用 Artlist 侧边栏
import MainContent from '@/components/Resource/MainContent.vue'; // <-- 使用新的内容组件
</script>

<style scoped>
/* 与 'src/pages/artlist/index.vue' 相同的布局样式 */
.resource-page {
  display: flex;
  width: 100%;
  min-height: 100vh;
  background-color: #F5F5F4; /* 使用项目主色调 */
  color: #333; /* 使用项目默认文字色 */
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
  /* 添加 padding，与 MainContent 的样式配合 */
  padding: 24px;
  box-sizing: border-box;
}

.content-component {
  flex-grow: 1; /* 占据剩余高度并允许滚动 */
  overflow-y: auto;
}

/* 移动端适配 */
@media (max-width: 768px) {
  .resource-page {
    flex-direction: column;
  }
  .sidebar-component {
    width: 100%;
    height: auto; /* 移动端不再是全高 */
    display: none; /* 可选：移动端隐藏侧边栏，通过汉堡菜单控制 */
  }
  .main-area {
    width: 100%;
  }
  .content-component {
    width: 100%;
  }
}
</style>