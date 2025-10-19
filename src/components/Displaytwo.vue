<template>
  <view class="section-wrapper">
    <view class="column text-column">
      <text class="section-title">渴望找到优秀的伙伴？</text>
      <text class="section-text">
        在HITeacher发现优秀伙伴，并组成学习小组，互相激励，共同成长
      </text>
      <!-- 替换为按钮，移除圆形箭头 -->
      <button class="custom-button custom-button-primary" @click="onFindPartnerClick">
        发现优秀伙伴
      </button>
    </view>
    <view class="column image-column">
      <view class="image-placeholder">[Doctor Measuring Height]</view>
    </view>
  </view>
</template>

<script setup lang="ts">
const onFindPartnerClick = () => {
  console.log('发现优秀伙伴按钮被点击了！');
  // 在这里添加你的点击逻辑
};
</script>

<style scoped>
/* 大部分样式与 MutationsSection 类似 */
.section-wrapper {
  display: flex;
  max-width: 1200px;
  margin: 0 auto;
  padding: 60px 20px;
  gap: 40px;
  align-items: center;
  background-color: #F5F5F4; /* 修改：更新背景色 */
  box-sizing: border-box;
}

.column {
  flex: 1;
  min-width: 300px;
}

.image-column {
  position: relative;
}

.image-placeholder {
  width: 100%;
  height: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #eee;
  color: #888;
  font-size: 16px;
}

.text-column {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.section-title {
  font-size: 42px;
  font-weight: 300;
  line-height: 1.2;
  color: #1f2937; /* 可选：根据设计调整标题颜色 */
}

.section-text {
  font-size: 16px;
  line-height: 1.7;
  color: #374151; /* 可选：根据设计调整文本颜色 */
}

/* 修改：按钮基础样式 - 调整高度、最大圆角、左对齐且宽度自适应 */
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
  align-self: flex-start; /* 关键：使按钮在 flex 容器中左对齐 */
  margin-left: 0; /* 关键：强制左边距为 0，防止任何继承或默认值 */
  /* margin-left: auto; 删除：这个是右对齐的属性 */
}

/* 新增：按钮焦点样式 */
.custom-button:focus {
  outline: none;
  /* focus:ring-2 focus:ring-offset-2 通常需要使用 box-shadow 实现 */
  box-shadow: 0 0 0 2px #fff, 0 0 0 4px #000; /* 示例 focus ring，颜色可调整 */
}

/* 修改：primary 按钮样式 (使用靛蓝色) */
.custom-button-primary {
  background-color: #1E3A8A; /* 修改：使用靛蓝色 */
  color: #fff; /* text-white */
}

/* 修改：primary 按钮悬停样式 (使用靛蓝色) */
.custom-button-primary:hover {
  background-color: transparent; /* hover:bg-transparent */
  color: #1E3A8A; /* hover:text-indigo-600 */
  border-color: #1E3A8A; /* hover:border-2 border-indigo-600 */
}

/* 移动端适配: 文本在图片上方 */
@media (max-width: 768px) {
  .section-wrapper {
    flex-direction: column-reverse; /* 图片在下 */
  }
}
</style>