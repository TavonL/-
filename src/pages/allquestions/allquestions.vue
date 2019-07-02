<template>
  <div class="container">
    <wux-row>
        <wux-col span="8" offset="4">
            <div style="font-size:64rpx">所有问题</div>
        </wux-col>
    </wux-row>
    <wux-white-space body-style="height: 26rpx" />
    <wux-search-bar clear maxlength="8" />
    <wux-white-space body-style="height: 20rpx" />
    <wux-row>
        <wux-col span="10" offset="1">
            <wux-cell title="标题文字1" is-link label="附加描述1"></wux-cell>
            <wux-cell title="标题文字2" is-link label="附加描述2"></wux-cell>
            <wux-cell title="标题文字3" is-link label="附加描述3"></wux-cell>
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
    clickHandle () {

    }
  }
}
</script>