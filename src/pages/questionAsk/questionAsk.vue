<template>
  <div class="container">
  <wux-select id="wux-select1" />
  <view class="page__bd">
      <wux-cell-group title="请选择问题类别：">
          <wux-cell title="类别" :extra="title1" @click="onClick1"></wux-cell>
      </wux-cell-group>
  </view>
  <div class="input">
     <wux-cell-group title="请输入您的问题：">
        <wux-cell hover-class="none">
              <wux-textarea hasCount rows="6" cursorSpacing="80" placeholder="请输入" />
          </wux-cell>
      </wux-cell-group>
  </div>
  <div class="camera" style="margin-top:5px " >
      <wux-row>
        <wux-col span="6" offset="5">
          <wux-image wux-class="image" shape="normal" width=50px height=50px src="../../../static/tabs/camera.gif" 
                loading="Loading" @click="Details" />  
          </wux-col>
      </wux-row>     
    </div>
    <div class="button">
      <wux-row>
        <wux-col span="6" offset="3">
            <wux-button block type="balanced" size="default" @click="clickbutton1">提交</wux-button>
        </wux-col>
      </wux-row>
    </div>
  </div>
  
</template>

<script>
import { $wuxSelect } from '../../../static/wux-ui/index'
export default {
  data(){
    return{
      title1: '',
    }
    
  },

  methods:{
    onClick1() {
            var that=this;
            $wuxSelect('#wux-select1').open({
                options: [
                    '粮油',
                    '茶叶',
                    '花卉',
                    '水产',
                    '畜牧',
                    '水果',
                    '蔬菜',
                    '桑蚕',
                    '食用菌',
                    '中药材',
                    '饲料',
                    '兽医',
                    '植保',
                    '植检',
                    '土壤',
                    '肥料',
                    '种子',
                    '生态',
                    '农机',
                    '能源'
                ],
                onConfirm: (value, index, options) => {
                    if (index !== -1) {
                       that.title1= options[index];    
                    }
                },
            })
        },
      }
}
</script>

<style scoped>
</style>