<template>
  <view>
    <!-- 1.0 搜索框 -->
    <navigator url="/pages/search/mani" class="btn" hover-class="none">
      <view class="btn-in">
        <icon class="btn-icon" type="search" size="16"></icon>
        搜索
      </view>
    </navigator>
    <!-- 2.0 轮播图 -->
    <swiper
      indicator-dots
      indicator-active-color="#fff"
      autoplay
      circular
      interval="2000"
    >
      <block v-for="(item,index) in imgUrls" :key="index">
        <swiper-item>
          <image mode="aspectFit" :src="item" class="slide-image"></image>
        </swiper-item>
      </block>
    </swiper>
  </view>
</template>

<script>
export default {
  data() {
    return {
  imgUrls: [
      'https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/banner1.png',
      'https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/banner2.png',
      'https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/banner3.png'
    ]
      }
    }
  }
</script>

<style>
/* 1.0 搜索框 */
.btn{
  background-color: #DC143C;
  padding: 20rpx;
}
.btn-in{
  height: 60rpx;
  background-color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 32rpx;
  color:#ccc;
  border-radius: 10rpx;
}
.btn-icon{
  margin-right: 20rpx;
}

/* 2.0 轮播图  */
.slide-image{
  width: 750rpx;
  height: 340rpx;
}
swiper{
  height: 340rpx;
}
</style>
