<template>
	<view class="uni-tab-bar">
		<scroll-view scroll-x class="uni-swiper-tab" :style="scrollStyle">
			<view v-for="(item,index) in tabBars" :key="index" :class="{active:currentIndex === index}" @tap="changeTab(index)"
			 class="swiper-tab-list" :style="scrollItemStyle">
				{{item.name}}  {{item.num?item.num:''}}
				<view class="swiper-tab-line"></view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		props:{
			tabBars:Array,
			currentIndex:Number,
			scrollStyle:{
				type:String,
				default:""
			},
			scrollItemStyle:{
				type:String,
				default:""
			}
		},
		methods:{
			changeTab(index){
				this.$emit("changeTab",index)
			}
		}
	}
</script>

<style scoped>
	.uni-swiper-tab {
		border-bottom: 1px solid #EEEEEE;
	}

	.uni-swiper-list {
		color: #969696;
		font-weight: bold;
	}

	.uni-swiper-tab .active {
		color: #343434;
	}

	.active .swiper-tab-line {
		border-bottom: 6upx solid #fede33;
		width: 70upx;
		margin: auto;
		border-top: 6upx solid #FEDE33;
		border-radius: 20upx;
	}
</style>
