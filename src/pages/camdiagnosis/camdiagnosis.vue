<template>
<view class='out'>
  <scroll-view scroll-y scroll-into-view='item2'>
    <view id='item1' class='item'>
      <view class='inner'>1</view>
    </view>
    <view id='item2' class='item'>
      <view class='inner'>2</view>
    </view>
    <view class='item'>
      <view class='inner'>3</view>
    </view>
    <view class='item'>
      <view class='inner'>4</view>
    </view>
  </scroll-view>
</view>
</template>

<script>
export default {
  data () {
    return {
      msg: 'Hello'
    }
  },

  methods: {
    clickHandle () {
      this.msg = 'Clicked!!!!!!'
    }
  }
}
</script>

<style scoped>
.out {
  background: #ddd;
}
/**设置高度就会出现纵向滚动条**/
.out scroll-view{
    height: 200px;
}

.out .item {
  height: 100px;
  border: 1px solid red;
  background: white;
  margin: 10px;
}

</style>