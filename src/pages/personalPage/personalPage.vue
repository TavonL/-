<template>
  <div class="container">
    <wux-divider position="left" text="个人信息" />
    <wux-row>
        <wux-col span="4" offset="1">
            <wux-image wux-class="image" shape="circle" width=113px height=113px src="../../../static/images/head.png" loading="Loading" />
        </wux-col>
        <wux-col span="7">
            <div style="margin-top:5px">昵称：{{username}}</div>
            <div style="margin-top:5px">用户身份：<span style="color:blue">{{useridentity}}</span></div>
            <div style="margin-top:5px">认证状态：<span style="color:red">{{confirmstatus}}</span></div>
            <wux-white-space body-style="height: 4px" />
            <wux-tag color="magenta" @click="clickbutton1">点此成为认证专家</wux-tag>
        </wux-col>
    </wux-row>
    <wux-divider position="left" text="农场记事" />
    <wux-row>
        <wux-col span="2" offset="2">
            <wux-button block type="balanced" size="small" @click="clickbutton2">我的提问</wux-button>
        </wux-col>
        <wux-col span="2" offset="1">
            <wux-button block type="energized" size="small" @click="clickbutton3">我的回答</wux-button>
        </wux-col>
        <wux-col span="2" offset="1">
            <wux-button block type="positive" size="small" @click="clickbutton4">我要记事</wux-button>
        </wux-col>
    </wux-row>
    <wux-white-space body-style="height: 25px" />
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
    <wux-white-space body-style="height: 10px" />
    <wux-row>
      <wux-col span="10">
            <wux-cell-group>
               <wux-cell hover-class="none">
                   <wux-textarea hasCount rows="6" cursorSpacing="80" placeholder="写写农场大小事儿..." />
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
</template>

<script>
export default {
  data () {
    return {
      username:'Unknown',
      useridentity:'Unknown',
      confirmstatus:'Unknown',
      timeAxis1: [
          {time: '2019年2月10日'},
          {time: '2019年2月16日'},
          {time: '2019年2月21日'},
          {time: '2019年2月27日'}
      ],
    }
  },

  methods: {
    clickbutton1 () {
      wx.navigateTo(
        {
          url:'/pages/expert/main'
        }
      )
    },
    clickbutton2 () {
      wx.navigateTo(
        {
          url:'/pages/myQuestions/main'
        }
      )
    },
    clickbutton3 () {
      wx.navigateTo(
        {
          url:'/pages/myAnswers/main'
        }
      )
    },
    clickbutton4 () {
      wx.pageScrollTo({            
        scrollTop: 5000,         
        duration: 300           
      })
    },
    clickbutton5 () {
      
    },
    clickbutton6 () {
      
    }
  }
}
</script>

<style scoped>

.message{
    display: inline-block;
    width: 100%;
    height: 450rpx;
  }
  .circle{
    margin-left: 28rpx;
    margin-right: 50rpx;
    display: inline-block;
    height: 50rpx;
    width: 50rpx;
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
    display: inline-block;
    width: 500rpx;
    height: 300rpx;
    margin-left:80rpx ;
    word-wrap: break-word;
    word-break: break-all;
    overflow: hidden;
  }
  .circle img{
    max-width:100%;
    max-height:100%;
  }

</style>