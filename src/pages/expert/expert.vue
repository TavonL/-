<template>
  <div class="container">
    <wux-row>
        <wux-col span="8" offset="4">
            <div style="font-size:32px">专家认证</div>
        </wux-col>
    </wux-row>

    <wux-row>
        <wux-col span="10" offset="1">
            <wux-cell hover-class="none">
                <wux-input clear label="真实姓名" placeholder="请输入您的真实姓名" />
            </wux-cell>
        </wux-col>
        <wux-col span="10" offset="1">
            <wux-cell hover-class="none">
                <wux-input clear label="身份证号" placeholder="请输入您的身份证号" />
            </wux-cell>
        </wux-col>
        <wux-col span="10" offset="1">
            <wux-select id="wux-select1" />
              <wux-cell title="认证领域" :extra="title1"  @click="onClick"></wux-cell>
        </wux-col>
        <wux-white-space body-style="height: 10px" />
        <wux-col span="10" offset="1">
            <div style="font-size:20px">请上传您的认证材料：</div>
        </wux-col>
        <wux-col span="10" offset="1">
            <wux-upload listType="picture-card" :defaultFileList="fileList" max="6" 
                url="https://www.skyvow.cn/api/common/file" @change="onChange" @success="onSuccess"
                @fail="onFail" @complete="onComplete" @preview="onPreview" @remove="onRemove">
            <text>Upload</text>
        </wux-upload>            
        </wux-col>  
    </wux-row>
    <view class="expert">
      <wux-button block type="positive" >点击认证</wux-button>
    </view>
  </div>
</template>

<script>
import { $wuxSelect } from '../../../static/wux-ui/index'
export default {
  data () {
    return {
       imageUrl:'',
       title1: '',
    }
  },

  methods: {
    onClick() {
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
             ],
             onConfirm: (value, index, options) => {
                if (index !== -1) {
                   that.title1 = options[index];    
                 }
             },
        })
    },
    onChange(e) {
        console.log('onChange', e)
        const file  = e.target.file
        if (file.status === 'uploading') {
            wx.showLoading()
        } 
        else if (file.status === 'done') {
            this.imageUrl=file.url;
        }
    },
    onSuccess(e) {
        console.log('onSuccess', e)
    },
    onFail(e) {
        console.log('onFail', e)
    },
    onComplete(e) {
        console.log('onComplete', e)
        wx.hideLoading()
    },
    onPreview(e) {
        console.log('onPreview', e)
        const file=e.detail
        const fileList = e.detail
        wx.previewImage({
            current: file.url,
            urls: fileList.map((n) => n.url),
        })
    },
    onRemove(e) {
        console.log('onRemove', e)
        const file=e.detail
        const fileList = e.detail
        wx.showModal({
            content: '确定删除？',
            success: (res) => {
                console.log('success');
            },
        })
    },
  }
}
</script>

<style scoped>
.expert{
    width: 100%;
    position: fixed;
    bottom: 0%;
    display: block;
    justify-content: center;
    align-items: center;
}
</style>