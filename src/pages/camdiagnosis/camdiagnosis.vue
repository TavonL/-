<template>
<div class="container">
  <view class="name">
    <wux-row>
        <wux-col span="7" offset="5" style="color:black">
            <div style="font-size:80rpx">{{tree}}</div>
        </wux-col>
    </wux-row>
  </view>
  <wux-white-space body-style="height: 15rpx" />
  <view class="sick">
    <wux-row>
        <wux-col span="4" offset="2" style="color:blue">
            <div style="font-size:65rpx">{{sick}}</div>
        </wux-col>
        <wux-col span="4" offset="2" style="color:red">
            <div style="font-size:65rpx">{{degree}}</div>
        </wux-col>
    </wux-row>
  <wux-white-space body-style="height: 15rpx" />
  <view class="list">
    <wux-row>
        <wux-col span="10" offset="1">
            <wux-cell title="标题文字1" is-link label="附加描述1"></wux-cell>
            <wux-cell title="标题文字2" is-link label="附加描述2"></wux-cell>
            <wux-cell title="标题文字3" is-link label="附加描述3"></wux-cell>
        </wux-col>
    </wux-row>
  </view>
  </view>
</div>
</template>

<script>
export default {

}
</script>

<style>

</style>

<script>
export default {
  data () {
    return {
      tree: '苹果',
      sick: '灰斑病',
      degree: '严重',
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


</style>