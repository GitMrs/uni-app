<template>
	<uview class="commom-list u-f animated fadeIn">
		<view class="commom-list-l">
			<image :src="item.userpic" mode="widthFix" lazy-load></image>
		</view>
		<view class="commom-list-r">
			<view class="u-f-aj u-f-jsb">
				<view class="u-f-aj">
					<view>{{item.username}}</view>
					<view class="tag-sex icon iconfont" :class="item.sex === 0 ? 'icon-nan' : 'icon-nv'">{{item.sex === 0 ? "男" : "女"}}</view>
				</view>
				<view class="u-f-aj">
					<view class="icon iconfont icon-zengjia"></view>关注
				</view>
			</view>
			<view>
			{{item.title}}
			</view>
			<view class="u-f-aj">
				<block v-if="item.video">
					<image :src="item.titlepic" mode="widthFix" lazy-load> </image>
					<view class="commom-list-play icon iconfont icon-bofang"></view>
						<view class="commom-list-playinfo">
							{{item.video.looknum}} 次播放 {{item.video.long}}
						</view> 
				</block>
				<block v-if="item.share">
					<view class="commom-list-share u-f-aj">
						<image :src="item.share.pic" mode="widthFix" lazy-load></image>
						<view class="">
							{{item.share.title}}
						</view>
					</view>
				</block>
				<block v-if="item.img">
					 <image :src="item.titlepic" mode="widthFix" lazy-load> </image>
				</block>
				<!-- 图片 -->
				<!-- <image src="../../static/datapic/22.jpg" mode="widthFix" lazy-load> </image> -->
				<!-- 视频 -->
				<!-- 	<view class="commom-list-play icon iconfont icon-bofang"></view>
					<view class="commom-list-playinfo">
						20w 次播放 2:25
					</view> -->
				<!-- 分享 -->
			<!-- 	<view class="commom-list-share u-f-aj">
					<image src="../../static/datapic/1.jpg" mode="widthFix" lazy-load></image>
					<view class="">
						哈哈哈哈哈哈哈哈哈哈哈哈
					</view>
				</view> -->
			</view>
			<view class="u-f-aj u-f-jsb">
				<view class="">
					{{item.addree}}
				</view>
				<view class="u-f-aj">
					<view class="u-f-aj">
						<view class="icon iconfont icon-fenxiang"></view>{{item.sharenum}}
					</view>
					<view class="u-f-aj">
						<view class="icon iconfont icon-pinglun1"></view>{{item.commentnum}}
					</view>
					<view class="u-f-aj">
						<view class="icon iconfont icon-dianzan1"></view>{{item.commentnum}}
					</view>
				</view>
			</view>
		</view>
	</uview>

</template>

<script>
	export default {
		props:{
			key:Number,
			item:Object
		},
		data() {
			return {

			};
		}
	}
</script>

<style>
.commom-list {
		border-bottom: 1px solid #eee;
		padding: 20upx;
	}

	.commom-list-l {
		flex-shrink: none;
		margin-right: 15upx;
	}

	.commom-list-l image {
		width: 90upx;
		height: 90upx;
		border-radius: 100%;
	}

	.commom-list-r {
		flex: 1;
		flex-shrink: none;
	}

	.commom-list-r>view:nth-of-type(1)>view:first-child {
		color: #999999;
		font-size: 30upx;
	}

	.tag-sex {
		background: #007AFF;
		color: #FFFFFF;
		height: 20upx;
		font-size: 16upx;
		padding: 2upx 15upx;
		margin-left: 10upx;
		border-radius: 20upx;
		line-height: 22upx;
	}

	.commom-list-r>view:nth-of-type(1)>view:last-child {
		background: #EEEEEE;
		font-size: 26upx;
		line-height: 26px;
		padding: 0upx 5upx;
		border-radius: 10upx;
	}

	.commom-list-r>view:nth-of-type(2) {
		font-size: 32upx;
		padding: 15upx 0;
	}

	.commom-list-r>view:nth-of-type(3) {
		position: relative;
		width: 100%;
	}

	.commom-list-play,
	.commom-list-playinfo {
		position: absolute;
	}

	.commom-list-r>view:nth-of-type(3)>image {
		width: 100%;
		border-radius: 10upx;
	}

	.commom-list-play {
		font-size: 130upx;
		color: #fff;
	}

	.commom-list-playinfo {
		position: absolute;
		bottom: 13upx;
		right: 10upx;
		padding: 3upx 10upx;
		border-radius: 5upx;
		background: rgba(0, 0, 0, 0.75);
		color: #fff;
	}

	.commom-list-r>view:nth-of-type(4)>view {
		color: #BBBBBB;
	}

	.commom-list-r>view:nth-of-type(4)>view:nth-of-type(2)>view {
		margin-left: 10upx;
		padding-left: 5upx;
	}

	.commom-list-share {
		background: #EEEEEE;
		padding: 20upx;
		width: 100%;
		/* flex: 1; */
		border-radius: 20upx;
	}

	.commom-list-share image {
		flex-shrink: none;
		width: 200upx;
		height: 150upx;
		border-radius: 5upx;
		margin-right: 18upx;
	}

	.commom-list-share view {
		flex-shrink: none;
		flex: 1;
	}


</style>
