<template>
	<view class="u-f-a paper-list animated fadeInLeft" @tap="openDetail">
		<view class="u-f-aj">
			<image :src="item.userpic" mode="widthFix" lazy-load></image>
		</view>
		<view>
			<view class="u-f-a u-f-jsb name">{{item.username}}
				<view class="time">{{item.time}}</view>
			</view>
			<view class="u-f-a u-f-jsb desc">{{item.msg}}
				<template v-if="item.noreadnum > 0">
					<uni-badge :text="item.noreadnum" type="error"></uni-badge>
				</template>
			</view>
		</view>
	</view>
</template>

<script>
	import uniBadge from "../../components/uni-badge/uni-badge.vue";
	export default {
		components: {
			uniBadge
		},
		props: {
			item: {
				type: Object
			},
			index: Number
		},
		methods:{
			openDetail(){
				uni.navigateTo({
					url:"../../pages/user-chat/user-chat"
				})
			}
		}
	}
</script>

<style>
	.paper-list {
		padding: 20upx;
		border-bottom: 1px solid #eee;
	}

	.paper-list>view image {
		height: 100upx;
		width: 100upx;
		flex-shrink: none;
		border-radius: 100%;
	}

	.paper-list>view:nth-of-type(2) {
		margin-left: 30upx;
		flex: 1;
	}

	.paper-list .name {
		font-size: 30upx;
	}

	.paper-list .time {
		color: #9E9E9E;
		font-size: 20upx;
	}

	.paper-list .desc {
		color: #999;
	}
</style>
