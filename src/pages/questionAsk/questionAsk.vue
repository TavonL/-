<template>
  <div class="container">
 

  <div class="camera" style="margin-top:5px " >
      <wux-row>
        <wux-col span="6" offset="5">
          <wux-image wux-class="image" shape="normal" width=50px height=50px src="../../../static/tabs/camera.gif" 
                loading="Loading" bind:click="Details" />  
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
  data: {
   
  },

  methods:{

  }
}
</script>

<style scoped>
</style>