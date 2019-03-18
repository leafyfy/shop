<template>
  <view>
    <seacht></seacht>
    <view>
        <classify-left class="div-left">
            左边
        </classify-left>
        <classify-right class="div-right">
            右边
        </classify-right>
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
.div-left{
    width: 200rpx;
}
.div-right{
    
}
</style>
