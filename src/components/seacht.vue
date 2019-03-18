<template>
  <!-- 1.0 搜索框 -->
  <navigator url="/pages/search/mani" class="btn" hover-class="none">
    <view class="btn-in">
      <icon class="btn-icon" type="search" size="16"></icon>搜索
    </view>
  </navigator>
</template>

<script>
export default {};
</script>

<style>
/* 1.0 搜索框 */
.btn {
  background-color: #dc143c;
  padding: 20rpx;
}
.btn-in {
  height: 60rpx;
  background-color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 32rpx;
  color: #ccc;
  border-radius: 10rpx;
}
.btn-icon {
  margin-right: 20rpx;
}
</style>
