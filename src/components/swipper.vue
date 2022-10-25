<template>
  <view
  @touchstart="handleTouchstart"
  @touchend="handleTouchend">
    <image  mode="widthFix" :src="imgThumb"></image>

  </view>
</template>

<script>
export default {
    data(){
        return{
            startTime:0,
            startX:0,
            endX:0
        }
    },
    props:{
        imgThumb:String
    },
    methods:{
        handleTouchstart(e){
            this.startTime = Date.now()
            this.startX = e.changedTouches[0].clientX
            this.startY = e.changedTouches[0].clientY
        },
        handleTouchend(e){
            const endTime = Date.now()
            const endX = e.changedTouches[0].clientX
            const endY = e.changedTouches[0].clientY
            if(endTime - this.startTime > 2000){
                return
            }
            let direction = ""
            if(Math.abs(this.startX-endX)>10)
            {
                direction = (this.startX - endX) > 0 ? "right" : "left"
            }
            else {return}
            this.$emit("swipAction",{direction})
        }
    }
}
</script>

<style>

</style>