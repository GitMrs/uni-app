<template>
	<view>
		<!-- 模糊背景 -->
			<view class="topic-bg">
				<image :src="item.titlepic" mode=""></image>
			</view>
			<!-- 话题信息 -->
			<view class="topic-info">
				<view class="topic-info-t u-f-a">
					<image :src="item.titlepic" mode="widthFix" lazy-load></image>
					<view># {{item.title}} #</view>
				</view>
				<view class="topic-info-m u-f-a">
					<view>动态 {{item.totalnum}}</view>
					<view>今日 {{item.todaynum}}</view>
				</view>
				<view class="topic-info-b">
					{{item.desc}}
				</view>
			</view>
		
	</view>
</template>

<script>
	export default {
		props:{
			item:{
				type:Object
			}
		},
		data() {
			return {
				
			};
		}
	}
</script>

<style scoped>
	.topic-bg {
		width: 100%;
		height: 300upx;
		position: relative;
		overflow: hidden;
	}

	.topic-bg image {
		width: 100%;
		position: absolute;
		filter: blur(10px);
	}

	.topic-info {
		padding:  0upx 25upx;
	}

	.topic-info-t {
		position: relative;
	}
	.topic-info-t image{
			width: 200upx;
			height: 200upx;
			border-radius: 20upx;
			position: absolute;
			top: -100upx;
			flex-shrink:none ;
	}
	.topic-info-t>view{
		font-size: 35upx;
		margin-left: 240upx;
		flex: 1;
		flex-shrink: none;
	}
	.topic-info-m {
		padding: 60upx 0 10upx 0;
	}
	.topic-info-m>view{
		margin-right: 20upx;
	}
	.topic-info-m>view{
		color: #CDCDCD;
		
	}
	.topic-info-b {
		padding-bottom: 10upx;
		color: 24upx;
		color: #A3A3A3;
	}
</style>
