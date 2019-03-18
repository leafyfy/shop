<template>
  <view>
    <seacht></seacht>
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
          <image mode="aspectFit" :src="item.image_src" class="slide-image"></image>
        </swiper-item>
      </block>
    </swiper>
    <!-- 3.0 分类 -->
    <view class="cate">
      <block
        v-for="(item,index) in cate"
        :key="index">
        <image class="cate-img"
          :src="item.image_src"
          mode="aspectFit">
        </image>
      </block>
    </view>
    <view class="divide"></view>
    <!-- 4.0 首页楼层 -->
  </view>
</template>

<script>
import seacht from "../../components/seacht"
export default {
  data() {      
    return {
  imgUrls: [],
  cate:[]
      }
    },
    components:{
      seacht
    },
    onLoad(){
      // 轮播图
      wx.request({
        url: 'https://www.zhengzhicheng.cn/api/public/v1/home/swiperdata', //开发者服务器接口地址",
        success: res => {
          this.imgUrls = res.data.message;
        }
      }),
      // 分类
      wx.request({
        url: 'https://www.zhengzhicheng.cn/api/public/v1/home/catitems', //开发者服务器接口地址",
        success: res => {
          this.cate = res.data.message;
        },
      });
    }
  }
</script>

<style>


/* 2.0 轮播图  */
.slide-image{
  width: 750rpx;
  height: 340rpx;
}
swiper{
  height: 340rpx;
}

/* 3.0 分类 */
.cate{
  height: 190rpx;
  display: flex;
  justify-content: space-around;
  align-items: center;
}
.cate-img{
  flex: 1;
  width: 128rpx;
  height: 140rpx;
}

/* 4.0 首页楼层 */
/* 隔离盒子 */
.divide{
width: 90rpx;
}
</style>
