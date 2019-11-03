<template>
	<view class="u-f-aj home-data">
		<view class="u-f-aj" v-for="(item,index) in homeData" :key="index"><view class="">{{item.num}}</view>{{item.name}}</view>
	</view>
</template>

<script>
	export default {
		props:{
			homeData:Array
		}
	}
</script>

<style scoped>
	.home-data{
		padding: 20upx 40upx;
	}
	.home-data>view{
		flex: 1;
		flex-direction: column;
		color: #989898;
	}
	.home-data>view>view{
		font-size: 32upx;
		color: #333;
	}
</style>
