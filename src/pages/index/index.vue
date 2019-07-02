<template>
  <div class="container">
    <div class="weather">
      <wux-row >
        <wux-col span="12">
           <text>城市 : {{weather.city.data}}</text>
           <text>天气 : {{weather.weather.data}}</text>
           <text>气温 : {{weather.temperature.data}}</text>
           <text>风速 : {{weather.winddirection.data}} {{weather.windpower.data}}</text>
           <text>湿度 : {{weather.humidity.data}}</text>        
       </wux-col>
     </wux-row> 
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
       weather: { },
    }     
  },

  methods: {
    Details(){
       wx.navigateTo({
         url:'/pages/hotbasicques/main'
       })
    }
  },

  created:function(){
      var that=this;
      var myAmap=new AMapWX({key: '9b2adb0e58b8817b531ab9d4ff287869'});
      myAmap.getWeather({
        success:function(data)
        {
          console.log(data);
          that.weather=data;
          console.log(that.weather.city.data);
        },
        fail: function(info){
          console.log(info);
        }
      })
    },
}
</script>

<style scoped>
 .classification scroll-view{
    height: 450px;
 }
 .weather {
  background-image: url(../../../static/images/sun.jpg);
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
  margin: 20px;
 }
</style>