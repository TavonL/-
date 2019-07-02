<template>
  <div class="container">
    <div class="weather">
      <wux-row >
        <wux-col span="12">
           <text>城 市 : {{weather.city.data}}</text>
           <text>天 气 : {{weather.weather.data}}</text>
           <text>气 温 : {{weather.temperature.data}}°C</text>
           <text>风 速 : {{weather.winddirection.data}} {{weather.windpower.data}}</text>
           <text>湿 度 : {{weather.humidity.data}}</text>
       </wux-col>
     </wux-row> 
    </div>
    <div v-if="!shouquan" style="margin-left:165rpx">
       <wux-white-space body-style="height: 30rpx" />
       <button open-type="getUserInfo" @getuserinfo="bindgetuserinfo" type="primary" size="mini">首次进入，请点此授权您的信息</button>
    </div>
    <view class="classification">
    <scroll-view scroll-y scroll-into-view='item2'>
    <wux-grids :bordered='false' col="2">
            <wux-grid thumb="../../../static/classification/rice.png" label="粮油" @click="Details" />
            <wux-grid thumb="../../../static/classification/tea.png" label="茶叶" @click="Details" />
            <wux-grid thumb="../../../static/classification/flower.png" label="花卉" @click="Details" />
            <wux-grid thumb="../../../static/classification/fish.png" label="水产" @click="Details" />
            <wux-grid thumb="../../../static/classification/cow.png" label="畜牧" @click="Details" />
            <wux-grid thumb="../../../static/classification/fruit.png" label="水果" @click="Details" />
            <wux-grid thumb="../../../static/classification/vegetable.png" label="蔬菜" @click="Details" />
            <wux-grid thumb="../../../static/classification/silkworm.png" label="桑蚕" @click="Details" />
            <wux-grid thumb="../../../static/classification/marshroom.png" label="食用菌" @click="Details" />
            <wux-grid thumb="../../../static/classification/chinesemed.png" label="中药材" @click="Details" />
            <wux-grid thumb="../../../static/classification/siliao.png" label="饲料" @click="Details" />
            <wux-grid thumb="../../../static/classification/veterinarian.png" label="兽医" @click="Details" />
            <wux-grid thumb="../../../static/classification/zhibao.png" label="植保" @click="Details" />
            <wux-grid thumb="../../../static/classification/book.png" label="植检" @click="Details" />
            <wux-grid thumb="../../../static/classification/soil.png" label="土壤" @click="Details" />
            <wux-grid thumb="../../../static/classification/fertilizer.png" label="肥料" @click="Details" />
            <wux-grid thumb="../../../static/classification/seeds.png" label="种子" @click="Details" />
            <wux-grid thumb="../../../static/classification/ecological.png" label="生态" @click="Details" />
            <wux-grid thumb="../../../static/classification/machine.png" label="农机" @click="Details" />
            <wux-grid thumb="../../../static/classification/energy.png" label="能源" @click="Details" />
    </wux-grids>
    </scroll-view>
    </view>
  </div>
</template>

<script>
import {AMapWX} from '../../../static/js/amap-wx'
export default {
  data(){
    return{
       weather: {},
       shouquan:false
    }     
  },

  beforeMount(){
    let oldstorage=wx.getStorageSync('shouquan')
    if(!oldstorage){
      wx.setStorage({
            key:'shouquan',
            data:{}
        })
    }else{
      this.shouquan=oldstorage
    }
    let usernamesto=wx.getStorageSync('username')
    if(!usernamesto){
      wx.setStorage({
        key:'username',
        data:{}
      })
    }else{
      wx.request({
            url: 'http://120.77.155.63:8080/user/login',
            data:{
              username:usernamesto,
              password:usernamesto
            },
            header: {
              'content-type': 'application/json'
            },
            success (res) {
               console.log(res.data)
               var uid =res.data.id
               var udegree=res.data.degree
               //var udegree=res.data.status
               wx.setStorage({
                  key:'userid',
                  data:uid
                })
               wx.setStorage({
                  key:'userdegree',
                  data:udegree
                })
                // wx.setStorage({
                //   key:'userstatus',
                //   data:ustatus
                // })
             }
        })
      }
  },

  methods: {
    Details(){
       wx.navigateTo({
         url:'/pages/hotbasicques/main'
       })
    },
    bindgetuserinfo: function (e) {
        console.log(e)
        var arr = JSON.parse(e.target.rawData)
        var nickname = arr.nickName
        this.shouquan=true
        wx.setStorage({
            key:'username',
            data:nickname
        })
        wx.request({
            url: 'http://120.77.155.63:8080/user/adduser',
            data:{
              username:nickname,
              password:nickname
            },
            header: {
              'content-type': 'application/json'
            },
            success (res) {
               console.log(res.data)
            }
        })
    },
  },

  created:function(){
      var that=this;
      var myAmap=new AMapWX({key: '9b2adb0e58b8817b531ab9d4ff287869'});
      myAmap.getWeather({
        success:function(data)
        {
          that.weather=data;
        },
        fail: function(info){
          console.log(info);
        }
      })
    },
}
</script>

<style scoped>
 .weather {
  background-image: url('https://s2.ax1x.com/2019/07/01/ZGSB1U.jpg');
  background-size:100% 100%;
  position:relative;
  top:0%;
  left:0%;
  right:0%;
  height:15%;
  font-size: 13px;
  padding-top: 3rpx;
  padding-left: 3rpx;
 }
 .weather text{
  display: block;
  margin: 40rpx;
  font-size:34rpx;
  color: white;
 }
 .classification scroll-view{
    height: 900rpx;
 }
</style>