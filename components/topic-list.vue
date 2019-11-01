<template>
	<view class="topic-list u-f animated fadeInLeft" @tap="goTopicDetail">
		<image :src="item.titlepic" mode="widthFix" lazy-load></image>
		<view class="">
			<view># {{item.title}} #</view>
			<view>{{item.desc}}</view>
			<view>动态 {{item.totalnum}} 今日 {{item.todayNum}}</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			item:{
				type:Object
			},
			index:{
				type:Number
			}
		},
		data() {
			return {
				
			};
		},
		methods:{
			goTopicDetail(){
				uni.navigateTo({
					url:"../../pages/topic-detail/topic-detail"
				})
			}
		}
	}
</script>

<style scoped>
	.topic-list {
		padding: 10upx 0;
		border-bottom: 1px solid #eee;
	}

	.topic-list image {
		width: 200upx;
		height: 200upx;
		border-radius: 10upx;
		margin-right: 20upx;
		flex-shrink: none;
	}

	.topic-list>view {
		color: #9E9E9E;
	}

	.topic-list>view>view:first-child {
		color: #000000;
		font-size: 32upx;
	}
</style>
