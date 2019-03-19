<template>
  <view>
    <seacht></seacht>
    <view class="cata">
      <scroll-view scroll-y class="cata-left">
        <block v-for="(item,index) in [1,2,3,4,5,6,7,8,9,1,2,3,4,5,6,7,8,91]" :key="index">
          <view class="item" :class="{ ative: index === tabIndex }" @tap="changeTabs(index)">大家电</view>
        </block>
      </scroll-view>

      <view class="cata-right">
        <view>
          电视
        </view>
        <view>
          <view>
            <image></image>
            <view>分类名称</view>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
import seacht from "../../components/seacht";
export default {
  data() {
    return {
      tabIndex: 0
    };
  },
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
  background-color: #abc;
  flex: 1;
}
</style>
