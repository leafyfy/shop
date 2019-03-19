<template>
  <view>
    <!-- 搜索框 -->
    <seacht></seacht>
    <!-- 内容区域 -->
    <view class="cata">
      <!-- 左侧栏 -->
      <scroll-view scroll-y class="cata-left">
        <block v-for="(item,index) in cata" :key="index">
          <view class="item" :class="{ ative: index === tabIndex }" @tap="changeTabs(index)">{{item.cat_name}}</view>
        </block>
      </scroll-view>
      <!-- 右侧栏 -->
      <scroll-view scroll-y class="cata-right">
        <!-- 右侧头部标题 -->
        <block v-for="(item,index) in rightdata" :key="index">
        <view class="cata-right-title">
          {{item.cat_name}}
        </view>
        <view class="cata-right-list">
          <block
            v-for="(subItem,subIndex) in item.children"
            :key="subIndex">
          <view class="cata-right-list-item">
            <!-- 商品图片 -->
            <image :src="subItem.cat_icon"></image>
            <!-- 商品名称 -->
            <view>{{subItem.cat_name}}</view>
          </view>
          </block>
        </view>
        </block>
      </scroll-view>
    </view>
  </view>
</template>

<script>
// 导入模块
import seacht from "../../components/seacht"
import request from "../../utils/request.js" 
export default {
  data() {
    return {
      tabIndex: 0,
      cata:[],
      rightdata:[]
    };
  },
  onLoad(){
    // 使用封装的request发请求
    request("https://www.zhengzhicheng.cn/api/public/v1/categories").then((res)=>{
      this.cata = res.data.message;
      this.rightdata = this.cata[this.tabIndex].children;
    })
  },
  // 注册事件
  methods: {
    changeTabs(index) {
      this.tabIndex = index;
      
    }
  },
  components: {
    seacht
  }
};
</script>

<style>
/* 左侧栏 */
.cata {
  display: flex;
  position: fixed;
  top: 100rpx;
  bottom: 0;
  left: 0;
  right: 0;
}
.cata-left {
  width: 200rpx;
  background-color: #f4f4f4;
  flex-shrink: 0;
}
.cata-left .item {
  text-align: center;
  line-height: 100rpx;
  border-bottom: 1rpx solid #ccc;
}
.cata-left .item.ative {
  color: #dc143c;
  position: relative;
}
.cata-left .item.ative::before {
  content: "";
  position: absolute;
  background-color: #dc143c;
  width: 10rpx;
  left: 0;
  top: 20rpx;
  bottom: 20rpx;
}
.cata-right {
  /* background-color: #abc; */
  flex: 1;
}
/* 右侧栏 */
.cata-right-title{
  text-align: center;
  padding:40rpx 0;
}
.cata-right-title::before,
.cata-right-title::after{
  content: "/";
  color: #ccc;
  margin: 0 20rpx;
}
.cata-right-list{
  display: flex;
  flex-wrap: wrap;
}
.cata-right-list-item{
  width: 33.333%;
  font-size: 30rpx;
  text-align: center;
  padding: 20rpx 0;
}
.cata-right-list-item image{
  width: 120rpx;
  height: 120rpx;
}
</style>
