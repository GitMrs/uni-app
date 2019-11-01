<template>
	<view class="tag-sex icon iconfont" :class="sex === 0 ? 'icon-nan' : 'icon-nv'">{{age}}</view>
</template>

<script>
	export default {
		props:{
			sex:{
				type:Number
			},
			age:{
				type:Number
			}
		}
	}
</script>

<style scoped>
	.tag-sex {
		background: #007AFF;
		color: #FFFFFF;
		height: 20upx;
		font-size: 16upx;
		width: 40upx;
		padding: 2upx 4upx;
		border-radius: 20upx;
		line-height: 22upx;
		flex-shrink:0 ;
	}
	.icon-nv{
		background: #FF698D !important;
	}
</style>
