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
		font-size: 20upx;
		width: 44upx;
		padding: 2upx 6upx;
		border-radius: 20upx;
		margin-left: 10upx;
		line-height: 20upx;
		flex-shrink:0 ;
	}
	.icon-nv{
		background: #FF698D !important;
	}
</style>
