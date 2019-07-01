<template>
  <div class="container" >
    <view class="timeline">
    <scroll-view scroll-y scroll-into-view='item2'>
    <wux-row>
        <wux-col span="11" offset="1">
          <div class="message" v-for="item in timeAxis1">
            <div class="circle"><img src="../../../static/images/circle2.png" alt=""></div><span class="time">{{item.time}}</span>
            <div class="lineborder">
              <img src="../../../static/images/farm.jpg">
                 <div class="blueBorder">
                    <div class="blueRadius">
                    </div>
                    <div class="blueRadius">
                   </div>
                 </div>
            </div>
          </div>
        </wux-col>
    </wux-row>
    </scroll-view>
    </view>
    <view class="Input">
    <wux-row>
      <wux-col span="10">
            <wux-cell-group>
               <wux-cell hover-class="none">
                   <wux-textarea hasCount rows="6" cursorSpacing="80" placeholder="写点什么吧..." />
               </wux-cell>
            </wux-cell-group>
      </wux-col>
      <wux-col span="2">
        <wux-row>
          <wux-col span="1" offset="4">
             <wux-image wux-class="image" shape="square" width=30px height=28px @click="clickbutton5" src="../../../static/images/camera.png" />
          </wux-col>
        </wux-row>
        <wux-white-space body-style="height: 10px" />
        <wux-row>
          <wux-col span="1" offset="4">
             <wux-image wux-class="image" shape="square" width=30px height=28px @click="clickbutton6" src="../../../static/images/send.png" />
          </wux-col>
        </wux-row>
      </wux-col>
     </wux-row>
    </view>
  </div>
</template>

<script>
export default {
  data () {
    return {
      timeAxis1: [
          {time: '2019年2月10日'},
          {time: '2019年2月16日'},
          {time: '2019年2月21日'},
          {time: '2019年2月27日'}
      ],
    }
  },

  methods: {
   
  }
}
</script>

<style scoped>
.timeline scroll-view{
    height: 450px;
}
.message{
    display: inline-block;
    width: 100%;
    height: 450rpx;
  }
  .circle{
    margin-left: 35rpx;
    margin-right: 50rpx;
    display: inline-block;
    height: 40rpx;
    width: 40rpx;
    float: left;
  }
  .lineborder{
    margin-left: 50rpx;
    display: inline-block;
    height: auto;
    width: 100%;
    left: 200rpx;
    border-left: 5rpx solid #999999;
  }
  .lineborder img{
    display: inline-block;
    width: 500rpx;
    height: 300rpx;
    margin-left:75rpx;
    margin-top:15rpx;
    margin-bottom: 15rpx;
  }
  .lineborder p{
    border-width: medium;
    border-color:#4D8AD7; 
    margin-left:80rpx ;
  }
  .circle img{
    max-width:100%;
    max-height:100%;
  }
  .blueBorder{
  display: inline-block;
  margin-left:75rpx ;
  width: 250px;
  height: 150px;
  border:2px solid rgba(63,174,174,1);
  border-radius: 20px;
  position: relative;
}
.blueBorder div{
  display: inline-block;
  position: absolute;
}
.blueRadius{
  display: inline-block;
  width: 12px;
  height: 12px;
  border-radius: 6px;
  background-color: rgba(63,174,174,1);
}

</style>