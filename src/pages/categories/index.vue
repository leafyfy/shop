<template>
  <view>
    <seacht></seacht>
    <view class="cod">
      <classify-left class="div-left">左边</classify-left>
      <classify-right class="div-right">右边</classify-right>
    </view>
  </view>
</template>

<script>
import seacht from "../../components/seacht";
export default {
  components: {
    seacht
  }
};
</script>

<style>
.cod {
  position: relative;
}
.div-left {
  width: 200rpx;
  position: absolute;
  top: 0rpx;
  bottom: 0rpx;
  left: 0rpx;
  right: 0rpx;
}
.div-right {
  display: flex;
  flex: 1;
}
</style>
