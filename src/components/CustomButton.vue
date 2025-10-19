<!-- components/CustomButton.vue -->
<template>
  <button
    type="button" 
    class="custom-button"
    :class="[
      baseClasses,
      variantClasses[variant],
      className
    ]"
    @click="handleClick"
  >
    <slot></slot>
  </button>
</template>

<script setup lang="ts">
// 定义 props
interface Props {
  variant?: 'primary' | 'secondary' | 'outline';
  className?: string;
}

withDefaults(defineProps<Props>(), {
  variant: 'primary',
  className: ''
});

// 定义 emit
const emit = defineEmits<{
  click: []
}>();

// 定义按钮变体的 CSS 类
const variantClasses = {
  primary: 'bg-gray-800 text-white hover:bg-transparent hover:text-gray-800 hover:border-2 border-gray-800',
  secondary: 'bg-white text-gray-800 hover:bg-transparent hover:text-gray-800 hover:border-2 border-gray-800',
  outline: 'bg-transparent text-gray-800 border-2 border-gray-800 hover:bg-gray-800 hover:text-white',
};

// 基础 CSS 类
const baseClasses = 'px-4 py-2 rounded-lg font-semibold transition-colors focus:outline-none focus:ring-2 focus:ring-offset-2 flex items-center justify-center';

// 点击处理函数
const handleClick = () => {
  emit('click');
};
</script>

<style scoped>
/* 如果你的全局样式或基础样式已经定义了这些通用类，可以省略 */
/* 这里是为了确保样式生效，特别是 transition 和 focus 效果 */
.custom-button {
  cursor: pointer;
  border: none; /* 确保 outline 样式中的 border 不被默认样式覆盖 */
  outline: none;
  /* transition-colors 在 Tailwind 中是 utility class，这里用 CSS 属性模拟 */
  transition: background-color 0.2s ease, color 0.2s ease, border-color 0.2s ease;
}

/* 你也可以将 baseClasses 的样式直接写在 .custom-button 上，如下：
.custom-button {
  @apply px-4 py-2 rounded-lg font-semibold transition-colors focus:outline-none focus:ring-2 focus:ring-offset-2 flex items-center justify-center;
  cursor: pointer;
}
*/
</style>