<template>
  <view class="footer-wrapper">
    <view class="footer-links">
      <view class="link-column">
        <text class="column-title">Security & Brand</text>
        <text class="link-item">Report Copyright Infringement</text>
        <text class="link-item">Report Security Issue</text>
        <text class="link-item">Trademark Notice</text>
      </view>
      <view class="link-column">
        <text class="column-title">Website</text>
        <text class="link-item">Accessibility</text>
        <text class="link-item">Digital Accessibility</text>
        <text class="link-item">Privacy statement</text>
      </view>
      <view class="link-column">
        <text class="column-title">Get In Touch</text>
        <text class="link-item">Contact Harvard</text>
        <text class="link-item">Maps & Directions</text>
        <text class="link-item">Jobs</text>
      </view>
    </view>

    <!-- 删除了 footer-logo 部分 -->

    <view class="footer-bottom">
      <text class="copyright">
        Copyright © 2025 HITeacher
      </text>
      <!-- 删除了 social-icons 部分 -->
    </view>
  </view>
</template>

<script setup lang="ts">
// 该组件目前不需要脚本
</script>

<style scoped>
.footer-wrapper {
  background-color: #1a1a1a; /* 保持深色背景 */
  color: #ccc; /* 保持文字颜色 */
  padding: 60px 20px; /* 调整了顶部内边距，因为删除了 logo 区域 */
  box-sizing: border-box;
}

.footer-links {
  display: flex;
  justify-content: space-between;
  max-width: 1000px;
  margin: 0 auto 40px;
  flex-wrap: wrap;
  gap: 30px;
}

.link-column {
  flex: 1;
  min-width: 200px;
  display: flex;
  flex-direction: column;
}

.column-title {
  font-size: 18px; /* 增加字体大小 */
  font-weight: bold;
  color: white; /* 保持标题颜色 */
  margin-bottom: 15px;
}

.link-item {
  font-size: 16px; /* 增加字体大小 */
  margin-bottom: 10px;
  cursor: pointer;
}

.link-item:hover {
  text-decoration: underline;
}

/* 删除了 .footer-logo 样式 */

.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1000px;
  margin: 0 auto;
  padding-top: 20px;
  border-top: 1px solid #444; /* 保持边框颜色 */
}

.copyright {
  font-size: 14px; /* 增加字体大小 */
}

/* 删除了 .social-icons 样式 */

/* 移动端适配 */
@media (max-width: 768px) {
  .footer-links {
    flex-direction: column;
  }
  .footer-bottom {
    flex-direction: column-reverse;
    gap: 20px;
    text-align: center;
  }
  /* 为移动端也调整字体大小 */
  .column-title {
    font-size: 16px; /* 移动端稍小一点 */
  }
  .link-item {
    font-size: 14px; /* 移动端稍小一点 */
  }
  .copyright {
    font-size: 12px; /* 移动端稍小一点 */
  }
}
</style>