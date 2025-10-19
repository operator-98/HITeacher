<template>
  <view class="hero-wrapper">
    <view class="nav-bar">
      <view class="nav-left">
        <!-- HITeacher Logo -->
        <view class="logo-container">
          <text class="logo-hi">HI</text>
          <text class="logo-teacher">Teacher</text>
        </view>
        <!-- 删除了 <text class="nav-link">Learn about our lawsuits...</text> -->
      </view>
      <view class="nav-right">
        <!-- 删除了 <view class="nav-item"> <text class="icon">🔍</text> <text>Search</text> </view> -->
        <!-- 添加“立刻开始”按钮，应用之前的按钮样式 -->
        <button class="custom-button custom-button-primary mobile-hidden" @click="onGetStartedClick">
          立刻开始
        </button>
      </view>
    </view>

    <view class="hero-content">
      <text class="hero-title">让大学学习更简单</text>
      <text class="hero-subtitle">
        立刻开始：查找课程学习资料，寻求同学学业支持，加入学习氛围小组...
      </text>
    </view>
  </view>
</template>

<script setup lang="ts">
// 移除了 backgroundImage 的引入

// 该组件目前不需要脚本逻辑
const onGetStartedClick = () => {
  console.log('立刻开始按钮被点击了！');
  // 在这里添加你的点击逻辑
};
</script>

<style scoped>
.hero-wrapper {
  position: relative;
  min-height: 90vh;
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  color: black; /* 改为黑色以适应白色背景 */
  background-color: white; /* 设置为白色背景 */
  /* 删除了 background-image 相关属性 */
}

/* .hero-wrapper::before { ... } 也已删除，因为不再需要遮罩 */

.nav-bar,
.hero-content {
  position: relative;
  z-index: 2; /* 确保内容在背景上方 */
  width: 100%;
  max-width: 1200px;
  box-sizing: border-box;
}

/* 导航栏样式 */
.nav-bar {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  padding: 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%; /* 确保 nav-bar 占满宽度 */
  max-width: 1200px; /* 与内容对齐 */
  box-sizing: border-box;
}

.nav-left {
  display: flex;
  align-items: center;
  gap: 20px;
}

/* HITeacher Logo 样式 */
.logo-container {
  display: flex;
  align-items: center;
  font-size: 24px;
  font-weight: bold;
  font-family: inherit;
}

.logo-hi {
  color: #ff4d4d; /* 红色 */
}

.logo-teacher {
  color: #4d79ff; /* 蓝色 */
}

.nav-right {
  display: flex;
  gap: 20px;
  align-items: center; /* 确保右侧内容垂直居中 */
}

/* 新增：按钮基础样式 (复用之前的样式) */
.custom-button {
  padding: 0.25rem 1rem; /* 调整高度 */
  border-radius: 2rem; /* 保持最大圆角 */
  font-weight: 600; /* font-semibold */
  transition: background-color 0.2s ease, color 0.2s ease, border-color 0.2s ease; /* transition-colors */
  border: none; /* 确保没有默认边框 */
  outline: none; /* 确保没有默认轮廓 */
  cursor: pointer; /* 鼠标悬停样式 */
  display: inline-flex; /* 关键：使用 inline-flex，使按钮宽度自适应内容 */
  align-items: center; /* items-center */
  justify-content: center; /* justify-center */
  text-align: center; /* 居中按钮文字 */
  border: 2px solid transparent; /* 为悬停效果预留边框空间 */
  /* 注意：这里没有 align-self，因为它在 nav-right (flex row) 里 */
  margin-left: 0; /* 关键：强制左边距为 0 */
}

/* 新增：按钮焦点样式 */
.custom-button:focus {
  outline: none;
  /* focus:ring-2 focus:ring-offset-2 通常需要使用 box-shadow 实现 */
  box-shadow: 0 0 0 2px #fff, 0 0 0 4px #000; /* 示例 focus ring，颜色可调整 */
}

/* 新增：primary 按钮样式 */
.custom-button-primary {
  background-color: #1f2937; /* bg-gray-800 */
  color: #fff; /* text-white */
}

/* 新增：primary 按钮悬停样式 */
.custom-button-primary:hover {
  background-color: transparent; /* hover:bg-transparent */
  color: #1f2937; /* hover:text-gray-800 */
  border-color: #1f2937; /* hover:border-2 border-gray-800 */
}

/* 新增：移动端隐藏按钮 */
.mobile-hidden {
  display: block; /* 默认显示 */
}

/* 英雄内容样式 */
.hero-content {
  max-width: 700px;
}

.hero-title {
  font-size: 80px;
  font-weight: 300;
  letter-spacing: 1px;
  display: block;
  margin-bottom: 20px;
  font-family: inherit;
}

.hero-subtitle {
  font-size: 18px;
  line-height: 1.7;
  font-family: inherit;
}

/* 移动端适配 */
@media (max-width: 768px) {
  .hero-wrapper {
    min-height: 100vh;
    padding-top: 150px; /* 为堆叠的 nav 留出空间 */
    text-align: left; /* 内容文字左对齐 */
  }
  .nav-bar {
    flex-direction: column;
    align-items: flex-start; /* 关键：使 nav-bar 内容左对齐 */
    padding: 15px 20px; /* 调整移动端 padding */
  }
  .nav-left {
    /* flex-direction: column; 如果需要 Logo 垂直排列，取消注释 */
    gap: 10px;
    /* text-align: center; 删除：因为 .hero-wrapper 已经设为 left */
  }
  .logo-container {
    font-size: 20px; /* 移动端稍小字体 */
  }
  .nav-right {
    width: 100%; /* 让右侧（现在是按钮）占满宽度，以便居右 */
    justify-content: flex-end; /* 将按钮推到右侧 */
    margin-top: 10px; /* 与 Logo 之间添加间距 */
  }
  .hero-title {
    font-size: 48px;
  }
  .hero-subtitle {
    font-size: 16px;
  }
  /* 隐藏移动端的“立刻开始”按钮 */
  .mobile-hidden {
    display: none;
  }
}
</style>