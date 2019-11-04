<template>
	<view class="">
		<view class="other-login u-f-aj">
			<view class="u-f-aj">
				<view class="icon iconfont icon-weixin"></view>
			</view>
			<view class="u-f-aj">
				<view class="icon iconfont icon-QQ"></view>
			</view>
			<view class="u-f-aj">
				<view class="icon iconfont icon-xinlangweibo"></view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		methods:{
			goLogin(){
				uni.navigateTo({
					url:"../../pages/home/home-login/home-login"
				})
			}
		}
	}
</script>

<style scoped>
	.other-login {
		padding: 20upx;
	}
	
	.other-login>view {
		flex: 1;
	}
	
	.other-login>view>view{
		width: 100upx;
		height: 100upx;
		border-radius: 100%;
		font-size: 44upx;
		color: #FFFFFF;
		text-align: center;
		line-height: 100upx;
		border: 1px solid;
	}
	.other-login .icon-QQ{
		background: #2CAEFC;
	}
	.other-login .icon-weixin{
		background: #2AD198;
	}
	.other-login .icon-xinlangweibo{
		background: #FC7729;
	}
</style>
