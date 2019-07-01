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
            <wux-cell hover-class="none">
                <wux-input clear label="认证领域" placeholder="请输入您的身份证号" />
            </wux-cell>
        </wux-col>
        <wux-col span="10" offset="1">
            <view class="sub-title"></view>
                 <wux-upload url="https://www.skyvow.cn/api/common/file" bind:change="onChange" bind:success="onSuccess"
                  bind:fail="onFail" bind:complete="onComplete">
            <button type="default">点此上传您的证明材料</button>
        </wux-upload>
        </wux-col>
    </wux-row>
  </div>
</template>

<script>
export default {
  data () {
    return {

    }
  },

  methods: {
    onChange(e) {
        console.log('onChange', e)
        const { file } = e.detail
        if (file.status === 'uploading') {
            this.setData({
                progress: 0,
            })
            wx.showLoading()
        } else if (file.status === 'done') {
            this.setData({
                imageUrl: file.url,
            })
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
    onProgress(e) {
        console.log('onProgress', e)
        this.setData({
            progress: e.detail.file.progress,
        })
    },
    onPreview(e) {
        console.log('onPreview', e)
        const { file, fileList } = e.detail
        wx.previewImage({
            current: file.url,
            urls: fileList.map((n) => n.url),
        })
    },
    onRemove(e) {
        const { file, fileList } = e.detail
        wx.showModal({
            content: '确定删除？',
            success: (res) => {
                if (res.confirm) {
                    this.setData({
                        fileList: fileList.filter((n) => n.uid !== file.uid),
                    })
                }
            },
        })
    },
  }
}
</script>