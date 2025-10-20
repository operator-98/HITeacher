<template>
  <view class="content-wrapper">
    <view class="header">
      <!-- 修改：标题 -->
      <text class="title">开始享受数字化的大学学习旅程~</text>
      <!-- 删除了 subscribe-btn-mobile 按钮 -->
      <!-- <button class="subscribe-btn-mobile">Subscribe Now</button> -->
    </view>

    <view class="card-grid">
      <view class="content-card">
        <view class="card-header">
          <text class="card-title">学习资源</text>
          <text class="arrow">↗</text>
        </view>
        <view class="image-placeholder image-card">
          <text>[学习资源 Placeholder]</text>
        </view>
      </view>

      <view class="content-card">
        <view class="card-header">
          <text class="card-title">优秀伙伴</text>
          <text class="arrow">↗</text>
        </view>
        <view class="image-placeholder video-card">
          <text>[优秀伙伴 Placeholder]</text>
        </view>
      </view>

      <view class="content-card">
        <view class="card-header">
          <text class="card-title">学习小组</text>
          <text class="arrow">↗</text>
        </view>
        <view class="image-placeholder voice-card">
          <text>[学习小组 Placeholder]</text>
        </view>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts"></script>

<style scoped>
.content-wrapper {
  padding: 24px;
}

.header {
  margin-bottom: 24px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.title {
  font-size: 24px;
  font-weight: bold;
}

/* 删除了 .subscribe-btn-mobile 样式 */

.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}

.content-card {
  background-color: #E5E7EB; /* 使用浅灰色卡片背景 */
  border-radius: 12px;
  padding: 20px;
  cursor: pointer;
  transition: background-color 0.2s;
}
.content-card:hover {
  background-color: #D1D5DB; /* 使用更浅的灰色悬停 */
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 16px;
}

.card-title {
  font-size: 20px;
  font-weight: bold;
}

.arrow {
  font-size: 24px;
  color: #6B7280; /* 使用中灰色箭头 */
}

.image-placeholder {
  width: 100%;
  height: 250px;
  border-radius: 8px;
  background-color: #D1D5DB; /* 使用浅灰色占位图背景 */
  display: flex;
  align-items: center;
  justify-content: center;
  color: #9CA3AF; /* 使用浅灰色占位图文字 */
  font-size: 14px;
  overflow: hidden;
  position: relative;
}

/* 为不同卡片类型定义特定的占位图样式（可选，当前都一样） */
.image-card {
  /* 可以添加特定样式 */
}
.video-card {
  /* 可以添加特定样式 */
}
.voice-card {
  /* 可以添加特定样式 */
}

/* 移动端适配 */
@media (max-width: 768px) {
  .header {
    flex-direction: column;
    align-items: flex-start;
    gap: 15px;
  }
  /* 删除了 .subscribe-btn-mobile 的移动端显示规则 */
  .card-grid {
    grid-template-columns: 1fr; /* 移动端单列 */
  }
}
</style>