<template>
  <div class="container">
    <wux-row>
        <wux-col span="4" offset="2">
            <div style="font-size:25px" @click="clickbutton1">{{tag1}}</div>
        </wux-col>
        <wux-col span="4" offset="1">
            <div style="font-size:25px;color:gray" @click="clickbutton2">{{tag2}}</div>
        </wux-col>
    </wux-row>
    <wux-white-space body-style="height: 10px" />
    <wux-row>
      <wux-col span="10" offset="1">
            <wux-cell title="标题文字1" is-link label="附加描述1"></wux-cell>
            <wux-cell title="标题文字2" is-link label="附加描述2"></wux-cell>
            <wux-cell title="标题文字3" is-link label="附加描述3"></wux-cell>
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
       tag1:'农技知识',
       tag2:'热门问题'
    }
  },

  methods: {
    clickbutton1 () {
      
    },
    clickbutton2 () {

    }
  }
}
</script>