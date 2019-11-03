<template>
	<view class="home-info u-f-aj u-f-jsb">
		<view class="u-f">
			<image :src="info.userpic" mode="widthFix" lazy-load></image>
			<view class="user-info">
				<view class="">{{info.username}}</view>
				<view class="">总访客 {{info.totalnum}} 今日 {{info.todaynum}}</view>
			</view>
		</view>
		<view class="icon iconfont icon-jinru" @tap="goSet"></view>
	</view>
</template>

<script>
	export default {
		props: {
			info: Object
		},
		data() {
			return {

			}
		},
		methods:{
			goSet(){
				uni.navigateTo({
					url:"../../pages/home/home-set/home-set"
				})
			}
		}
	}
</script>

<style scoped>
	.home-info {
		padding: 20upx 40upx;
	}

	.home-info>view>image {
		flex-shrink: 0;
		height: 100upx;
		width: 100upx;
		border-radius: 100%;
		margin-right: 15upx;
	}

	.home-info>view:first-child {
		flex: 1;
	}

	.home-info>view:last-of-type {
		width: 30upx;
	}

	.user-info>view:first-child {
		font-size: 32upx;
	}

	.user-info>view:last-child {
		color: #BBBBBB;
	}
</style>
