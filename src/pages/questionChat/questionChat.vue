<template>
  <div class="container" >
    <div class="timeline">
    <wux-row>
        <wux-col span="11" offset="1">
          <div class="message" v-for="item in timeAxis1">
            <div class="circle"><img src="../../../static/images/timeline.png" alt=""></div><span class="time">{{item.time}}</span>
            <div class="lineborder">
              <img src="../../../static/images/farm.jpg">
              <p>content</p>
            </div>
          </div>
        </wux-col>
    </wux-row>
    </div>
    <div class="input">
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
    </div>
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
.message{
    display: block;
    width: 100%;
    height: 450rpx;
  }
  .circle{
    margin-left: 28rpx;
    margin-right: 50rpx;
    display: block;
    height: 50rpx;
    width: 50rpx;
    float: left;
  }
  .lineborder{
    margin-left: 50rpx;
    display: block;
    height: 400rpx;
    width: 100%;
    left: 200rpx;
    border-left: 5rpx solid #999999;
  }
  .lineborder img{
    display: block;
    width: 500rpx;
    height: 300rpx;
    margin-left:75rpx;
    margin-top:15rpx;
    margin-bottom: 15rpx;
  }
  .lineborder p{
    margin-left:80rpx ;
  }
  .circle img{
    max-width:100%;
    max-height:100%;
  }
</style>