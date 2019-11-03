<template>
	<view>
		<!-- 动画 -->
		<view class="index-list animated fadeInLeft fast">
			<view class="list-user u-f-a u-f-jsb">
				<view class="u-f-a">
					<image :src="items.userpic" mode="widthFix" lazy-load></image>
					{{items.username}}
				</view>
				<view>
					<view class="u-f-a" v-if="items.isguanzhu" @tap="cancelGuanzhu">
						<view class="icon iconfont icon-guanbi"></view>取消
					</view>
					<view class="u-f-a" v-else @tap="guanzhu">
						<view class="icon iconfont icon-zengjia"></view>关注
					</view>
				</view>
			</view>
			<view @tap="gotoDetail">
				<view class="list-title" >
					<view>{{items.title}}</view>
				</view>
				<!-- 图片 -->
				<view v-if="items.type === 'img'" class="list-image">
					<image :src="items.titlepic" mode="widthFix" lazy-load></image>
				</view>
				<view v-else class="list-video u-f-aj">
					<image :src="items.titlepic" mode="widthFix" lazy-load></image>
					<view class="video-play icon iconfont icon-bofang"></view>
					<view class="video-playinfo">{{items.playnum + '次播放 ' + items.long}}</view>
				</view>
			</view>
		
			<view class="list-bottom u-f-a u-f-jsb">
				<view class="u-f-a">
					<view class="u-f-a" :class="{active:items.infonum.index === 1}" @tap="ding">
						<view class="icon iconfont icon-icon_xiaolian-mian"></view>{{items.infonum.ding}}
					</view>
					<view class="u-f-a" :class="{active:items.infonum.index === 2}" @tap="cai">
						<view class="icon iconfont icon-kulian"></view>{{items.infonum.cai}}
					</view>
				</view>
				<view class="u-f-a">
					<view class="u-f-a">
						<view class="icon iconfont icon-pinglun1"></view>{{items.comment}}
					</view>
					<view class="u-f-a">
						<view class="icon iconfont icon-zhuanfa"></view>{{items.share}}
					</view>
				</view>
			</view>
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
		data(){
			return {
				items:this.item
			}
		},
		methods:{
			//关注
			guanzhu(){
				// console.log(this.item)
				// this.item = {}
				this.items.isguanzhu = true
				uni.showToast({
					title:"关注成功"
				})
				console.log(this.item)
			},
			//取消
			cancelGuanzhu(){
				console.log(this.item)
				this.items.isguanzhu = false;
				uni.showToast({
					title:"取消成功"
				})
				console.log(this.item)
			},
			//顶
			ding(){
				if(this.items.infonum.index == 1) return;
				this.items.infonum.index = 1;
				this.items.infonum.cai-=1
				this.items.infonum.ding+=1
			},
			//踩
			cai(){
				if(this.items.infonum.index == 2) return;
				this.items.infonum.index = 2;
				this.items.infonum.ding-=1
				this.items.infonum.cai+=1
			},
			gotoDetail(){
				uni.navigateTo({
					url:"../../pages/detail/detail?detailData=" + JSON.stringify(this.item)
				})
				// console.log('进入详情也')
			}
			
		}
	}
</script>

<style scoped>
	.index-list {
		padding: 20upx;
		border-bottom: 2px solid #fafafa;
	}

	.list-user>view:first-child {

		color: #999999;
	}

	.list-user>view:first-child image {
		width: 80upx;
		height: 80upx;
		border-radius: 100%;
		margin-right: 10upx;
	}

	.list-user>view:last-child>view {
		background: #f4f4f4;
		border-radius: 20upx;
		color: black;
		padding: 0 20upx;
	}

	.list-title>view {
		padding-top: 15upx;
		font-size: 30upx;
		font-weight: 600;
	}

	.list-image image {
		width: 100%;
		border-radius: 20upx;
	}

	.list-video {
		width: 100%;
		position: relative;
		border-radius: 20upx;
	}

	.list-video image {
		width: 100%;
	}

	.list-video .video-play {
		position: absolute;
		font-size: 130upx;
		color: #fff;
	}

	.list-video .video-playinfo {
		position: absolute;
		bottom: 30upx;
		right: 30upx;
		background: rgba(51, 51, 51, 0.7);
		color: #fff;
		border-radius: 15upx;
		padding: 0upx 30upx;
	}

	.list-bottom {
		padding: 10upx 0;
		color: #BEBEBE;
	}

	.list-bottom>view>view>view {
		margin: 0 10upx;
	}

	.list-bottom .active {
		color: #f8b446;
	}
</style>
