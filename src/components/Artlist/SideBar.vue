<template>
  <view class="sidebar">
    <!-- Logo 永远显示 -->
    <view class="logo">
      <text class="logo-hi">HI</text>
      <text class="logo-teacher">Teacher</text>
    </view>

    <!-- 导航列表，在移动端隐藏 -->
    <view class="nav-list">
      <!-- 修改：为主页按钮也添加点击事件，并根据当前页面路径动态添加 active 类 -->
      <!-- 使用 isCurrentPage 方法来判断是否为当前页面 -->
      <view class="nav-item" :class="{ active: isCurrentPage('artlist') }" @click="navigateToArtlist">
        <text>主页</text>
      </view>
      <view class="nav-item" :class="{ active: isCurrentPage('resource') }" @click="navigateToResource">
        <text>学习资源</text>
      </view>
      <view class="nav-item" :class="{ active: isCurrentPage('partners') }" @click="navigateToPartners">
        <text>优秀伙伴</text>
      </view>
      <view class="nav-item" :class="{ active: isCurrentPage('groups') }" @click="navigateToGroups">
        <text>学习小组</text>
      </view>
    </view>

    <!-- 删除了原来的用户列表 (user-list) -->
  </view>
</template>

<script setup lang="ts">
// 定义跳转函数
const navigateToArtlist = () => {
  uni.navigateTo({
    url: '/pages/artlist/index', // 跳转到 artlist 页面
    success: (res) => {
      console.log('跳转到主页 (artlist) 成功', res);
    },
    fail: (err) => {
      console.error('跳转到主页 (artlist) 失败', err);
      uni.showToast({
        title: `页面跳转失败: ${err.errMsg || '未知错误'}`,
        icon: 'none',
        duration: 2000
      });
    }
  });
};

const navigateToResource = () => {
  uni.navigateTo({
    url: '/pages/resource/index',
    success: (res) => {
      console.log('跳转到学习资源页面成功', res);
    },
    fail: (err) => {
      console.error('跳转到学习资源页面失败', err);
      uni.showToast({
        title: `页面跳转失败: ${err.errMsg || '未知错误'}`,
        icon: 'none',
        duration: 2000
      });
    }
  });
};

// 假设的其他页面跳转函数
const navigateToPartners = () => {
  uni.navigateTo({
    url: '/pages/partners/index', // 请根据实际路径修改
    success: (res) => {
      console.log('跳转到优秀伙伴页面成功', res);
    },
    fail: (err) => {
      console.error('跳转到优秀伙伴页面失败', err);
      uni.showToast({
        title: `页面跳转失败: ${err.errMsg || '未知错误'}`,
        icon: 'none',
        duration: 2000
      });
    }
  });
};

const navigateToGroups = () => {
  uni.navigateTo({
    url: '/pages/groups/index', // 请根据实际路径修改
    success: (res) => {
      console.log('跳转到学习小组页面成功', res);
    },
    fail: (err) => {
      console.error('跳转到学习小组页面失败', err);
      uni.showToast({
        title: `页面跳转失败: ${err.errMsg || '未知错误'}`,
        icon: 'none',
        duration: 2000
      });
    }
  });
};

// 定义一个方法，用于判断当前页面是否是传入的页面标识符
const isCurrentPage = (pageIdentifier: string) => {
  const pages = getCurrentPages(); // 获取页面栈
  if (pages.length > 0) {
    const currentPage = pages[pages.length - 1]; // 获取当前页面实例
    const currentRoute = currentPage.route; // 获取当前页面路径
    console.log('SideBar 检测到当前页面路径:', currentRoute);

    // 根据页面路径判断对应的标识符
    // 请确保这里的路径判断逻辑与你的实际文件路径和 pages.json 配置一致
    // 例如，如果页面路径是 'pages/artlist/index'，则标识符是 'artlist'
    if (currentRoute) {
      if (currentRoute.includes('artlist')) {
        return pageIdentifier === 'artlist';
      } else if (currentRoute.includes('resource')) {
        return pageIdentifier === 'resource';
      } else if (currentRoute.includes('partners')) {
        return pageIdentifier === 'partners';
      } else if (currentRoute.includes('groups')) {
        return pageIdentifier === 'groups';
      }
    }
  }
  // 如果无法获取路径或路径不匹配，则默认返回 false
  // 或者根据你的默认页面逻辑返回 true，例如：
  // return pageIdentifier === 'artlist'; // 如果 artlist 是默认主页
  return false;
};

// 可选：如果你想在 SideBar 组件显示时也更新状态（例如在页面通过浏览器后退按钮返回时）
// 但这通常不如每次渲染时调用 isCurrentPage 来得直接
// import { onMounted, onUpdated } from 'vue';
// onMounted(() => {
//   // 组件挂载时检查一次
//   // isCurrentPage('...'); // 不直接调用，而是通过模板中的 :class
// });
// onUpdated(() => {
//   // 组件更新时检查一次（这可能不够精确，依赖模板响应式更新）
//   // isCurrentPage('...'); // 不直接调用，而是通过模板中的 :class
// });

</script>

<style scoped>
/* ... 保持原有的样式不变 ... */
.sidebar {
  width: 100%;
  /* height: 100vh; /1* 移动端时可能不需要占满视口高度 *1/ */
  background-color: #E5E7EB; /* 使用浅灰色背景 (与 MainContent 保持一致) */
  padding: 20px;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  color: #6B7280; /* 使用中灰色文字 */
}

.logo {
  font-size: 28px;
  font-weight: bold;
  color: #1E3A8A; /* 使用靛蓝色整体，子元素再分别设置 */
  margin-bottom: 30px; /* 桌面端时的下边距 */
  padding-left: 10px;
  display: flex; /* 使 HI 和 Teacher 并排 */
  align-items: center; /* 垂直居中对齐 */
}

.logo-hi {
  color: #B91C1C; /* 使用深红色 */
}

.logo-teacher {
  color: #1E3A8A; /* 使用靛蓝色 */
}

.nav-list {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

/* 删除了 .user-list 样式 */

.nav-item {
  display: flex;
  align-items: center;
  /* gap: 12px; /1* 修改：移除图标后的间距 *1/ */
  padding: 10px 10px;
  border-radius: 8px;
  font-size: 15px;
  font-weight: 500;
  cursor: pointer; /* 添加光标样式 */
  transition: all 0.2s;
}

.nav-item:hover {
  background-color: #D1D5DB; /* 使用浅灰色悬停背景 */
  color: #1f2937; /* 使用深灰色悬停文字 */
}

.nav-item.active {
  background-color: #D1D5DB; /* 使用浅灰色激活背景 */
  color: #1f2937; /* 使用深灰色激活文字 */
}

/* 删除了 .icon 样式 */

/* 移动端适配：隐藏导航列表，调整 Logo 间距 */
@media (max-width: 768px) {
  .nav-list {
    display: none; /* 隐藏导航按钮列表 */
  }
  .logo {
    margin-bottom: 10px; /* 调整移动端 Logo 下边距，因为没有导航项了 */
    padding-left: 0; /* 调整移动端 Logo 左侧内边距 */
  }
}
</style>