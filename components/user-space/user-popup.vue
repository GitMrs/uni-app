<template>
	<view>
		<view class="paper-left-popup-mask" v-show="show" @tap="hidePopup"></view>
		<view class="paper-left-popup" v-show="show">
			<view @tap="lahei" class="u-f-a" hover-class="paper-left-popup-h"><view class="icon iconfont icon-sousuo"></view>拉黑</view>
			<view  @tap="beizhu" class="u-f-a" hover-class="paper-left-popup-h"><view class="icon iconfont icon-qingchu"></view>备注</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			show:{
				type:Boolean
			}
		},
		methods:{
			hidePopup(){
				this.$emit("hidePopup",false)
			},
			lahei(){
				this.$emit("lahei",false)
			},
			beizhu(){
				this.$emit("beizhu",false)
			}
		}
	}
</script>

<style scoped>
	.paper-left-popup{
		position: fixed;
		right: 0;
		top: 130upx;
		background: #FFFFFF;
		z-index: 2000;
		width: 55%;
		box-shadow: 1upx 1upx 20upx 2upx #CCCCCC;
	}
	.paper-left-popup-mask{
		position: fixed;
		left: 0;
		top: 0;
		right: 0;
		bottom: 0;
		z-index: 1999;
	}
	.paper-left-popup>view{
		padding:20upx;
		font-size: 35upx;
	}
	.paper-left-popup>view>view{
		padding-left: 10upx;
	}
	.paper-left-popup-h{
		background: #EEEEEE;
	}
</style>

