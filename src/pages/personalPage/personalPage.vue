<template>
  <div class="container">
    <wux-divider position="left" text="个人信息" />
    <wux-row>
        <wux-col span="4" offset="1">
            <wux-image wux-class="image" shape="circle" width=220rpx height=220rpx src="../../../static/images/head.png" loading="Loading" />
        </wux-col>
        <wux-col span="7">
            <div style="margin-top:2rpx">我的昵称：{{username}}</div>
            <div style="margin-top:10rpx">用户身份：<span style="color:blue">{{useridentity}}</span></div>
            <div style="margin-top:10rpx">认证状态：<span style="color:red">{{userstatus}}</span></div>
            <wux-white-space body-style="height: 10rpx" />
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
    <wux-white-space body-style="height: 35rpx" />
    <wux-row>
        <wux-col span="11" offset="1">
          <div class="message" v-for="item in timeAxis1">
            <div class="circle"><img src="../../../static/images/timeline.png" alt=""></div><span class="time">{{item.time}}</span>
            <div class="lineborder">
              <img src="../../../static/images/farm.jpg">
              <p>content...content...content...content...content...content...content...content</p>
            </div>
          </div>
        </wux-col>
    </wux-row>
    <wux-white-space body-style="height: 20rpx" />
    <wux-row>
      <wux-col span="12">
            <wux-cell-group>
               <wux-cell hover-class="none">
                   <wux-textarea hasCount rows="5" cursorSpacing="80" placeholder="写点儿什么吧..." />
               </wux-cell>
            </wux-cell-group>
      </wux-col>
    </wux-row>
    <wux-white-space body-style="height: 20rpx" />
    <wux-row>
      <wux-col span="8" offset="1">
            <wux-upload listType="picture-card" :defaultFileList="fileList" max="2" 
                url="https://www.skyvow.cn/api/common/file" @change="onChange" @success="onSuccess"
                @fail="onFail" @complete="onComplete" @preview="onPreview" @remove="onRemove">
            <text style="font-size:30rpx">上传图片</text>
          </wux-upload>            
      </wux-col> 
      <wux-col span="2">
        <wux-button block type="balanced" size="small" >提交</wux-button>
      </wux-col>
    </wux-row>
    <wux-white-space body-style="height: 20rpx" />
  </div>
</template>

<script>
export default {
  data () {
    return {
      username:'',
      useridentity:'',
      userstatus:'',
      timeAxis1: [
          {time: '2019年2月10日'},
          {time: '2019年2月16日'},
          {time: '2019年2月21日'},
          {time: '2019年2月27日'}
      ],
    }
  },

   beforeMount(){
    let uname=wx.getStorageSync('username')
    if(!uname){
      wx.setStorage({
            key:'username',
            data:{}
        })
    }else{
      this.username=uname
    }
    let udegree=wx.getStorageSync('userdegree')
    if(!udegree){
      wx.setStorage({
            key:'userdegree',
            data:{}
        })
    }else{
      if(udegree==3){
         this.useridentity='普通用户'
      }
      else if(udegree==2){
         this.useridentity='农技专家'
      }
      else if(udegree==1){
         this.useridentity='管理员'
      }
      else{
         this.useridentity='Unknown'
      }
    }
    // let ustatus=wx.getStorageSync('userstatus')
    // if(!ustatus){
    //   wx.setStorage({
    //         key:'userstatus',
    //         data:{}
    //     })
    // }else{
    //   this.userstatus=ustatus
    // }
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
    width:500rpx;
    height: auto;
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