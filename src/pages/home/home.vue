<template>
	<view>首页
	 	<swipper @swipAction="handleSwipAction" :imgThumb="curSrc"> </swipper>
	 
	 
	 </view>
</template>

<script>
import swipper from "@/components/swipper";
	export default {
		data(){
			return{
				defaultSrc:"../static/pictures/t.jpg",
				src:["../static/pictures/t.jpg",
					"../static/pictures/1.jpg",
					"../static/pictures/2.jpg",
					"../static/pictures/3.jpg",
					"../static/pictures/4.jpg",
					"../static/pictures/5.jpg",
					"../static/pictures/6.jpg"],
				curSrc:"",
				curId:0
			}
		},
		methods: {
		handleSwipAction(e)
		{
			if(e.direction==="left"&&this.curId>0)
			{
				this.curId--;
			}
			else if(e.direction==="right"&&this.curId<this.src.length-1)
			{
				this.curId++;
			}
			else{
				uni.showToast({
					title:"没有数据了",
					icon:"none"
				})
			}
			this.curSrc = this.src[this.curId]
		}
	
		},
		components:{
			swipper:swipper
		},
		onShow(){
			this.curSrc = this.defaultSrc
		}
		 
	}
</script>

<style lang="scss">
	
	
</style>
