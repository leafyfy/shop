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
    <!-- 4.0 首页楼层 -->
    <block v-for="(item,index) in floor" :key="index">
    <view class="divide"></view>
      <view class="floor">
        <view class="floor-title">
          <image
            :src="item.floor_title.image_src">
          </image>
        </view>
        <!-- 商品盒子 -->
        <view class="floor-body">
          <!-- 商品左侧 -->
          <view class="floor-body-left">
            <image :src="item.product_list[0].image_src">
            </image>
          </view>
          <!-- 商品右测 -->
          <view class="floor-body-right">
            <block v-for="(subItem,subIndex) in item.product_list" :key="subIndex">
              <image 
              v-if="subIndex !== 0"
              :src="item.product_list[subIndex].image_src">
              </image>
            </block>
          </view>
        </view>
      </view>
    </block>
  </view>
</template>

<script>
import seacht from "../../components/seacht"
export default {
  data() {      
    return {
  imgUrls: [],
  cate:[],
  floor:[]
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
        }
      }),
      // 楼层
      wx.request({
        url: 'https://www.zhengzhicheng.cn/api/public/v1/home/floordata', //开发者服务器接口地址",
        success: res => {
          this.floor = res.data.message;
        }
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
  height: 20rpx;
  background-color: #f4f4f4;
}
.floor-title image{
  width: 750rpx;
  height: 60rpx;
  background-color: #f4f4f4;
}
.floor-body{
  display: flex;
  padding:20rpx 0 20rpx 20rpx;
}
.floor-body-left image{
  width: 232rpx;
  height: 386rpx;
margin-right: 10rpx;
}
.floor-body-right image{
  width: 232rpx;
  height: 188rpx;
  margin-right: 10rpx;
}
</style>
