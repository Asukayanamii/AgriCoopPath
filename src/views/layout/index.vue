<template>
  <div class="common-layout">
    <el-container>
      <!-- Header 区域 - 农业无人机主题 -->
      <el-header class="header">
        <span class="title">农业无人机路径规划算法展示系统</span>
        <span class="right_tool">
          <a href="">
            <el-icon><EditPen /></el-icon> 修改密码 &nbsp;&nbsp;&nbsp; |  &nbsp;&nbsp;&nbsp;
          </a>
          <a href="">
            <el-icon><SwitchButton /></el-icon> 退出登录
          </a>
        </span>
      </el-header>
      
      <el-container>
        <!-- 左侧菜单 - 农业无人机业务维度 -->
        <el-aside width="200px" class="aside">
          <el-menu router>
            <!-- 首页菜单 -->
            <el-menu-item index="/index">
              <el-icon><Promotion /></el-icon> 系统首页
            </el-menu-item>
            
            <!-- 地图与地块管理 -->
            <el-sub-menu index="/land">
              <template #title>
                <el-icon><MapLocation /></el-icon> 地图与地块管理
              </template>
              <el-menu-item index="/land/map">
                <el-icon><Picture /></el-icon> 电子地图加载
              </el-menu-item>
              <el-menu-item index="/land/plot">
                <el-icon><Crop /></el-icon> 地块信息管理
              </el-menu-item>
              <el-menu-item index="/land/boundary">
                <el-icon><Fence /></el-icon> 地块边界编辑
              </el-menu-item>
            </el-sub-menu>
            
            <!-- 路径规划算法核心模块 -->
            <el-sub-menu index="/algorithm">
              <template #title>
                <el-icon><Algorithm /></el-icon> 路径规划算法
              </template>
              <el-menu-item index="/algorithm/basic">
                <el-icon><LineChart /></el-icon> 基础路径算法
              </el-menu-item>
              <el-menu-item index="/algorithm/optimize">
                <el-icon><TrendCharts /></el-icon> 优化路径算法
              </el-menu-item>
              <el-menu-item index="/algorithm/compare">
                <el-icon><ScaleToOriginal /></el-icon> 算法效果对比
              </el-menu-item>
            </el-sub-menu>

            <!-- 无人机参数配置 -->
            <el-sub-menu index="/drone">
              <template #title>
                <el-icon><Airplane /></el-icon> 无人机参数配置
              </template>
              <el-menu-item index="/drone/info">
                <el-icon><Setting /></el-icon> 无人机型号管理
              </el-menu-item>
              <el-menu-item index="/drone/parameter">
                <el-icon><Sliders /></el-icon> 飞行参数设置
              </el-menu-item>
              <el-menu-item index="/drone/constraint">
                <el-icon><Lock /></el-icon> 飞行约束配置
              </el-menu-item>
            </el-sub-menu>

            <!-- 路径仿真与结果展示 -->
            <el-sub-menu index="/simulation">
              <template #title>
                <el-icon><VideoPlay /></el-icon> 路径仿真与结果
              </template>
              <el-menu-item index="/simulation/preview">
                <el-icon><Eye /></el-icon> 路径仿真预览
              </el-menu-item>
              <el-menu-item index="/simulation/result">
                <el-icon><DataBoard /></el-icon> 规划结果统计
              </el-menu-item>
              <el-menu-item index="/simulation/log">
                <el-icon><Document /></el-icon> 仿真日志查看
              </el-menu-item>
            </el-sub-menu>

            <!-- 系统管理 -->
            <el-sub-menu index="/system">
              <template #title>
                <el-icon><Tools /></el-icon> 系统管理
              </template>
              <el-menu-item index="/system/user">
                <el-icon><User /></el-icon> 用户管理
              </el-menu-item>
              <el-menu-item index="/system/config">
                <el-icon><Gear /></el-icon> 系统配置
              </el-menu-item>
            </el-sub-menu>
          </el-menu>
        </el-aside>
        
        <!-- 主内容区 -->
        <el-main>
          <router-view></router-view>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script setup>
// 按需导入Element Plus图标（需确保项目已安装并注册Element Plus）
import { 
  EditPen, SwitchButton, Promotion, MapLocation, 
  Picture, Crop, Fence, Algorithm, LineChart, 
  TrendCharts, ScaleToOriginal, Airplane, Setting, 
  Sliders, Lock, VideoPlay, Eye, DataBoard, 
  Document, Tools, User, Gear 
} from '@element-plus/icons-vue'
</script>

<style scoped>
/* 农业主题渐变（青绿色系，贴合农业+科技感） */
.header {
  background-image: linear-gradient(to right, #006400, #228B22, #32CD32, #90EE90, #98FB98);
}

.title {
  color: white;
  font-size: 36px;
  font-family: 微软雅黑, 楷体;
  line-height: 60px;
  font-weight: bolder;
}

.right_tool {
  float: right;
  line-height: 60px;
}

a {
  color: white;
  text-decoration: none;
}

a:hover {
  color: #f0f9ff;
  text-decoration: underline;
}

.aside {
  width: 220px;
  border-right: 1px solid #e5e7eb;
  height: calc(100vh - 60px); /* 适配不同屏幕高度 */
  background-color: #f9fafb;
}

/* 优化菜单样式，贴合农业主题 */
:deep(.el-menu) {
  border-right: none;
  height: 100%;
  background-color: #f9fafb;
}

:deep(.el-sub-menu__title) {
  color: #166534;
  font-weight: 500;
}

:deep(.el-menu-item) {
  color: #14532d;
}

:deep(.el-menu-item.is-active) {
  color: #ffffff;
  background-color: #228B22;
}
</style>