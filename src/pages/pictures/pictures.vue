<template>
	<view>图集
		<scroll-view scroll-y class="pictures"></scroll-view>
		<uni-segmented-control :current="current" :values="items" @clickItem="onClickItem" styleType="button" activeColor="#4cd964"></uni-segmented-control>
		<view class="content">
            <view v-if="current === 0" >
                <view v-for="s in src1" :key="s">
				<image :src="s"></image>
				</view>
            </view>
            <view v-if="current === 1">
                <view v-for="s in src2" :key="s">
				<image :src="s"></image>
				</view>
            </view>
            <view v-if="current === 2">
                <view v-for="s in src3" :key="s">
				<image :src="s"></image>
				</view>
            </view>
        </view>



	</view>
	
</template>

<script>
import uniSegmentedControl from "@/components/uni-segmented-control.vue"
	export default {
		data(){
			return{
				items: ['选项1', '选项2', '选项3'],
        		current: 0,
				src1:["../../static/pictures/t.jpg",
					"../../static/pictures/1.jpg"],
				src2:["../../static/pictures/2.jpg",
					"../../static/pictures/3.jpg"],
				src3:["../../static/pictures/4.jpg",
					"../../static/pictures/5.jpeg",
					"../../static/pictures/6.jpg"]

			}
		},
		methods: {
		onClickItem(e) {
      if (this.current != e.currentIndex) {
        this.current = e.currentIndex;
      			}
		}
		},
		components:{
			uniSegmentedControl
		}
		
	}
</script>

<style lang="scss">
	
	
</style>
