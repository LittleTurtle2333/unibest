<route lang="json5">
{
  style: {
    navigationBarTitleText: '关于',
    navigationStyle: 'custom', // 开启自定义导航栏
  },
}
</route>

<script lang="ts" setup>
import RequestComp from './components/request.vue'
import UploadComp from './components/upload.vue'

// 获取屏幕边界到安全区域距离
const { safeAreaInsets } = uni.getSystemInfoSync()
function toSubPage() {
  uni.navigateTo({
    url: '/pages-sub/demo/index',
  })
}

// 奇怪：同样的代码放在 vue 里面不会校验到错误，放在 .ts 文件里面会校验到错误
// const testOxlint = (name: string) => {
//   console.log('oxlint')
// }
// testOxlint('oxlint')
</script>

<template>
  <view>
    <fg-navbar>关于</fg-navbar>
    <view
      class="overflow-hidden bg-white px-4 pt-2"
      :style="{ marginTop: `${safeAreaInsets?.top}px` }"
    >
      <view class="mt-8 text-center text-3xl">
        鸽友们好，我是
        <text class="text-red-500">
          菲鸽
        </text>
      </view>
      <!-- <button @click="toSubPage()">去分包</button> -->
      <view class="test-css">
        测试 scss 样式
      </view>
      <RequestComp />
      <UploadComp />
    </view>
  </view>
</template>

<style lang="scss" scoped>
.test-css {
  // 16rpx=>0.5rem
  padding-bottom: 16rpx;
  // mt-4=>1rem=>16px;
  margin-top: 16px;
  text-align: center;
}
</style>
