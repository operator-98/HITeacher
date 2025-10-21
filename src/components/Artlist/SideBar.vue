<template>
  <view class="sidebar">
    <!-- Logo -->
    <view class="logo">
      <text class="logo-hi">HI</text>
      <text class="logo-teacher">Teacher</text>
    </view>

    <!-- 导航列表 -->
    <view class="nav-list">
      <view
        class="nav-item"
        :class="{ active: currentPage === 'artlist' }"
        @click="navigateToArtlist"
      >
        <text>主页</text>
      </view>

      <view
        class="nav-item"
        :class="{ active: currentPage === 'resource' }"
        @click="navigateToResource"
      >
        <text>学习资源</text>
      </view>

      <view
        class="nav-item"
        :class="{ active: currentPage === 'profile' }"
        @click="navigateToProfile"
      >
        <text>个人资料</text>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

// 当前激活页面 key：'artlist' | 'resource' | 'profile'
const currentPage = ref('artlist')

// 更新本地状态（供内部/外部调用）
const updateCurrentPage = (pagePath: string) => {
  currentPage.value = pagePath
  // 方便调试
  // console.log('[Sidebar] updateCurrentPage ->', pagePath)
}

/**
 * 帮助函数：尝试从当前路由堆栈里推断当前页面标识
 * 兼容 uni-app 常见 getCurrentPages() 返回结构
 */
const detectCurrentPageFromRoute = () => {
  try {
    // @ts-ignore getCurrentPages 是运行时 API
    const pages = getCurrentPages && getCurrentPages()
    if (pages && pages.length) {
      const last = pages[pages.length - 1]
      // last.route 在 uni-app 中通常是 pages/xxx/xxx
      const route = last.route || last.__route || last.$route?.path || ''
      if (route) {
        if (route.includes('/pages/profile')) return 'profile'
        if (route.includes('/pages/resource')) return 'resource'
        if (route.includes('/pages/artlist')) return 'artlist'
      }
    }
  } catch (e) {
    // ignore
  }
  return null
}

// ========== 导航函数：在跳转前后同步状态 ==========
const navigateToArtlist = () => {
  updateCurrentPage('artlist')
  uni.navigateTo({
    url: '/pages/artlist/index',
    success: () => {
      // 主动通知（防止某些页面没有在 onShow 里 emit）
      uni.$emit('updateSidebarPage', 'artlist')
    },
    fail: (err) => {
      console.error('navigateToArtlist fail', err)
      uni.showToast({ title: '页面跳转失败', icon: 'none' })
    }
  })
}

const navigateToResource = () => {
  updateCurrentPage('resource')
  uni.navigateTo({
    url: '/pages/resource/index',
    success: () => uni.$emit('updateSidebarPage', 'resource'),
    fail: (err) => {
      console.error('navigateToResource fail', err)
      uni.showToast({ title: '页面跳转失败', icon: 'none' })
    }
  })
}

const navigateToProfile = () => {
  updateCurrentPage('profile')
  uni.navigateTo({
    url: '/pages/profile/index',
    success: () => uni.$emit('updateSidebarPage', 'profile'),
    fail: (err) => {
      console.error('navigateToProfile fail', err)
      uni.showToast({ title: '页面跳转失败', icon: 'none' })
    }
  })
}

// ========== 生命周期：初始化时尝试从路由推断当前页面，并订阅全局事件 ==========
onMounted(() => {
  // 1) 尝试从路由堆栈推断
  const detected = detectCurrentPageFromRoute()
  if (detected) updateCurrentPage(detected)

  // 2) 订阅事件：页面可以 emit 'updateSidebarPage' 来同步侧边栏
  uni.$on('updateSidebarPage', (pagePath: string) => {
    if (pagePath) updateCurrentPage(pagePath)
  })
})

onUnmounted(() => {
  uni.$off('updateSidebarPage')
})
</script>

<style scoped>
.sidebar {
  width: 100%;
  background-color: #f3f4f6;
  padding: 24px 16px;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  gap: 24px;
  border-radius: 20px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
}

.logo {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 28px;
  font-weight: 700;
  padding-left: 10px;
}

.logo-hi {
  color: #b91c1c;
}

.logo-teacher {
  color: #1e3a8a;
}

.nav-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

/* 导航项：最大圆角、平滑过渡 */
.nav-item {
  display: flex;
  align-items: center;
  padding: 12px 20px;
  border-radius: 9999px;
  font-size: 16px;
  font-weight: 500;
  cursor: pointer;
  color: #374151;
  background-color: transparent;
  transition: all 0.2s ease;
}

/* 悬停与激活样式 */
.nav-item:hover {
  background-color: #dbeafe;
  color: #1e3a8a;
}

/* 激活：深色背景 + 白字 */
.nav-item.active {
  background-color: #1e3a8a;
  color: #ffffff;
  box-shadow: 0 2px 6px rgba(30, 58, 138, 0.3);
}

/* 响应式：窄屏时横向展示 */
@media (max-width: 768px) {
  .sidebar {
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    padding: 12px 16px;
    border-radius: 0;
  }

  .logo {
    font-size: 22px;
    padding-left: 0;
  }

  .nav-list {
    flex-direction: row;
    gap: 8px;
  }

  .nav-item {
    font-size: 14px;
    padding: 8px 14px;
  }
}
</style>
