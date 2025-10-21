<template>
  <view class="profile-wrapper">
    <text class="main-title">个人资料</text>

    <view class="settings-content">
      <view class="form-column">
        <!-- 新版输入框部分 -->
        <view class="form-section">
          <label class="form-label">昵称</label>
          <view class="modern-input">
            <input
              v-model="nickname"
              type="text"
              placeholder="请输入昵称"
              maxlength="15"
            />
          </view>
        </view>

        <view class="form-section">
          <label class="form-label">个性签名</label>
          <view class="modern-input">
            <textarea
              v-model="bio"
              maxlength="80"
              rows="2"
              placeholder="写一句展示你的风格～"
            ></textarea>
          </view>
          <text class="char-count">{{ bio.length }}/80</text>
        </view>

        <!-- 头像与背景 -->
        <view class="form-section">
          <label class="form-label">头像</label>
          <view class="button-group">
            <view class="custom-button" @click="changeAvatar">更改头像</view>
          </view>
        </view>

        <view class="form-section">
          <label class="form-label">背景</label>
          <view class="button-group">
            <view class="custom-button" @click="changeBackground">更改背景</view>
          </view>
        </view>

        <!-- 退出登录 -->
        <view class="form-section">
          <label class="form-label">账户操作</label>
          <view class="button-group">
            <view class="custom-button logout-button" @click="logout">退出登录</view>
          </view>
        </view>
      </view>

      <!-- 右侧实时预览 -->
      <view class="preview-column">
        <label class="form-label">预览</label>
        <view class="preview-card">
          <view class="preview-header">
            <view class="avatar-placeholder">[AVATAR]</view>
            <view class="status-adder">
              <text class="status-icon">+</text>
              <text>添加状态</text>
            </view>
          </view>

          <view class="preview-user-info">
            <text class="preview-name">{{ nickname || '未命名用户' }}</text>
            <text class="preview-bio">{{ bio || '这个人很神秘，还没有留下个性签名。' }}</text>
          </view>

          <!-- 保存信息按钮现在使用 custom-button，宽度自适应 -->
          <view class="custom-button save-button" @click="saveProfile">保存信息</view>
        </view>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const nickname = ref<string>('')
const bio = ref<string>('')

// 模拟点击事件
const changeAvatar = () => {
  console.log('点击更改头像')
  // 实际业务逻辑...
}

const changeBackground = () => {
  console.log('点击更改背景')
}

const logout = () => {
  console.log('点击退出登录')
}

const saveProfile = () => {
  console.log('点击保存信息')
}
</script>

<style scoped>
.profile-wrapper {
  background-color: #f5f5f4;
  color: #333;
  padding: 20px 40px;
  height: 100%;
  box-sizing: border-box;
}

.main-title {
  font-size: 24px;
  font-weight: 700;
  color: #1f2937;
  margin-bottom: 20px;
  display: block;
}

.settings-content {
  display: flex;
  gap: 40px;
}
.form-column {
  flex: 2;
}
.preview-column {
  flex: 1;
  min-width: 280px;
}

.form-section {
  margin-bottom: 24px;
}
.form-label {
  font-size: 12px;
  color: #6b7280;
  font-weight: 600;
  margin-bottom: 8px;
  display: block;
}

/* 美观输入框 */
.modern-input {
  background-color: #ffffff;
  border: 1px solid #d1d5db;
  border-radius: 16px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05);
  padding: 8px 16px;
  transition: all 0.2s ease;
}
.modern-input:focus-within {
  border-color: #3b82f6;
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.15);
}
.modern-input input,
.modern-input textarea {
  width: 100%;
  border: none;
  outline: none;
  font-size: 15px;
  color: #111827;
  background-color: transparent;
  resize: none;
  font-family: inherit;
}
.modern-input textarea {
  height: 48px;
}
.modern-input input::placeholder,
.modern-input textarea::placeholder {
  color: #9ca3af;
}

.char-count {
  font-size: 12px;
  color: #9ca3af;
  text-align: right;
  display: block;
  margin-top: 5px;
}

/* 自定义按钮组 */
.button-group {
  display: flex;
  flex-direction: column;
  align-items: flex-start; /* 左对齐 */
  gap: 10px;
}

/* 自定义按钮样式 */
.custom-button {
  background-color: #1e3a8a;
  color: white;
  font-size: 14px;
  border: none;
  border-radius: 9999px;
  padding: 10px 20px;
  cursor: pointer;
  line-height: normal;
  width: auto; /* 关键：自适应宽度 */
  text-align: center;
  user-select: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  transition: background-color 0.2s ease;
  box-sizing: border-box; /* 确保padding不增加总宽度 */
}

.custom-button:hover {
  background-color: #1c3a7a;
}

.custom-button:active {
  background-color: #1a3770;
}

.logout-button {
  background-color: #b91c1c;
}

.logout-button:hover {
  background-color: #a81a1a;
}

.logout-button:active {
  background-color: #961717;
}

/* 预览 */
.preview-card {
  background-color: #e5e7eb;
  border-radius: 16px;
  padding: 20px;
  box-sizing: border-box; /* 确保padding不增加总宽度 */
}
.preview-header {
  display: flex;
  align-items: flex-start;
  margin-bottom: 15px;
}
.avatar-placeholder {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  background-color: #d1d5db;
  color: #6b7280;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 12px;
  flex-shrink: 0;
}
.status-adder {
  display: flex;
  align-items: center;
  gap: 5px;
  font-size: 13px;
  color: #6b7280;
  cursor: pointer;
  border: 1px dashed #9ca3af;
  padding: 5px 8px;
  border-radius: 9999px;
  margin-left: auto;
}
.status-icon {
  font-size: 16px;
  font-weight: bold;
}
.preview-user-info {
  border-top: 1px solid #d1d5db;
  padding-top: 15px;
}
.preview-name {
  font-size: 20px;
  font-weight: 700;
  color: #1f2937;
  display: block;
}
.preview-bio {
  font-size: 14px;
  color: #6b7280;
  display: block;
  margin-top: 8px;
  word-wrap: break-word;
}
/* 移除 save-button 的 width: 100% 和 margin-top */
.save-button {
  /* width: 100%; <- 删除此行 */
  background-color: #1e3a8a;
  color: white;
  text-align: center;
  padding: 12px 20px; /* 调整 padding 与 custom-button 一致 */
  border-radius: 9999px;
  font-size: 14px;
  font-weight: 500;
  border: none;
  /* margin-top: 20px; <- 删除此行 */
  cursor: pointer;
  transition: background-color 0.2s ease;
  width: auto; /* 确保覆盖可能的继承值 */
  margin-top: 20px; /* 如果需要与上面内容的间距，可以保留 */
}

.save-button:hover {
  background-color: #1c3a7a;
}

.save-button:active {
  background-color: #1a3770;
}

/* 响应式 */
@media (max-width: 992px) {
  .settings-content {
    flex-direction: column;
  }
}
@media (max-width: 768px) {
  .profile-wrapper {
    padding: 20px;
  }
}
</style>