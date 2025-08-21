<script setup>
import { ref } from 'vue'

const activeIndex = ref('/')

// 处理Bug反馈点击事件
const handleBugReport = (event) => {
  event.preventDefault() // 阻止默认路由行为
  event.stopPropagation() // 阻止事件冒泡
  window.open('https://github.com/lingyjava/auto-coder/issues', '_blank')
}
</script>

<template>
  <el-menu :default-active="activeIndex" class="el-menu" mode="horizontal" :ellipsis="false" router>
    <div class="logo-container">
      <img class="logo-image" src="@/assets/logo.png" alt="logo" />
      <span class="logo-text">𝑨𝒖𝒕𝒐 𝑪𝒐𝒅𝒆𝒓 𝑾𝒆𝒃</span>
    </div>
    <div class="flex-grow-1" />

    <el-menu-item index="/"> 首页 </el-menu-item>
    <el-menu-item index="/document"> 关于 </el-menu-item>
    <div class="custom-menu-item" @click="handleBugReport">Bug反馈</div>

    <!-- 分割线 -->
    <el-divider direction="vertical" style="height: 60%; margin: auto 10px" />

    <!-- icon -->
    <el-link href="https://github.com/lingyjava/auto-coder" target="_blank" style="margin: 0 15px">
      <img src="@/assets/github.svg" style="width: 25px; height: 25px" alt="github" />
    </el-link>
  </el-menu>
</template>

<style lang="scss" scoped>
.flex-grow-1 {
  flex-grow: 1;
}

.el-menu {
  padding: 0 15%;
}

// Logo区域样式
.logo-container {
  display: flex;
  align-items: center;
  height: 60px;

  .logo-image {
    width: 45px;
    height: 45px;
    object-fit: contain;
  }

  .logo-text {
    margin-left: 12px;
    font-size: 20px;
    font-weight: bold;
    color: #303133;
    white-space: nowrap;
    line-height: 1;
  }
}

// 自定义菜单项样式
.custom-menu-item {
  height: 60px;
  line-height: 60px;
  padding: 0 20px;
  color: #303133;
  cursor: pointer;
  transition: color 0.3s;
  display: inline-flex;
  align-items: center;
  font-size: 14px;

  &:hover {
    color: #409eff;
  }
}

// 菜单项样式
:deep(.el-menu--horizontal) {
  .el-menu-item {
    height: 60px;
    line-height: 60px;
    padding: 0 20px;

    &:hover {
      background-color: transparent;
      color: #409eff;
    }
  }
}
</style>
