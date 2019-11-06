<template>
	<view v-if="show" class="animated fadeIn faster">
		<view class="more-share-model" @tap="closeShare"></view>
		<view class="more-share">
			<view class="more-share-title u-f-aj">分享到</view>
			<scroll-view scroll-x="true" class="more-share-body u-f-aj">
				<block v-for="(item,index) in providerList" :key="index">
					<view class="more-share-item u-f-aj" hover-class="more-share-hove" @tap="share(item)">
						<view class="icon iconfont" :class="['icon-'+ item.zIcon,' more-share-' + item.zClass]"></view>
						<view>{{item.name}}</view>
					</view>
				</block>
			</scroll-view>
			<view class="more-share-bottom u-f-aj" @tap="closeShare">取消</view>
		</view>

	</view>
</template>

<script>
	export default {
		props: {
			show: Boolean
		},
		data() {
			return {
				shareText: 'uni-app可以同时发布成原生App、小程序、H5，邀请你一起体验！',
				href: "https://uniapp.dcloud.io",
				image: '',
				shareType: 1, //1:文字2：图片0：图文5小程序
				providerList: []
			}
		},
		mounted() {
			uni.getProvider({
				service: 'share',
				success: (e) => {
					let data = []
					for (let i = 0; i < e.provider.length; i++) {
						switch (e.provider[i]) {
							case 'weixin':
								data.push({
									name: '微信好友',
									id: 'weixin',
									zIcon: "weixin",
									zClass: "weixin",
									sort: 0
								})
								data.push({
									name: '朋友圈',
									id: 'weixin',
									zIcon: "weixin",
									zClass: "pyq",
									type: 'WXSenceTimeline',
									sort: 1
								})
								break;
							case 'sinaweibo':
								data.push({
									name: '新浪微博',
									zIcon: "xinlangweibo",
									zClass: "weibo",
									id: 'sinaweibo',
									sort: 2
								})
								break;
							case 'qq':
								data.push({
									name: 'QQ',
									id: 'qq',
									zIcon: "QQ",
									zClass: "qq",
									sort: 3
								})
								break;
							default:
								break;
						}
					}
					this.providerList = data.sort((x, y) => {
						return x.sort - y.sort
					});
					// console.log(this.providerList)
				},
				fail: (e) => {
					console.log('获取分享通道失败', e);
					uni.showModal({
						content: '获取分享通道失败',
						showCancel: false
					})
				}
			});
		},
		onLoad() {
			console.log("111111")
			// 
		},
		methods: {
			closeShare() {
				this.$emit("closeShare")
			},
			async share(e) {
				console.log('分享通道:' + e.id + '； 分享类型:' + this.shareType);

				if (!this.shareText && (this.shareType === 1 || this.shareType === 0)) {
					uni.showModal({
						content: '分享内容不能为空',
						showCancel: false
					})
					return;
				}

				if (!this.image && (this.shareType === 2 || this.shareType === 0)) {
					uni.showModal({
						content: '分享图片不能为空',
						showCancel: false
					})
					return;
				}

				let shareOPtions = {
					provider: e.id,
					scene: e.type && e.type === 'WXSenceTimeline' ? 'WXSenceTimeline' : 'WXSceneSession', //WXSceneSession”分享到聊天界面，“WXSenceTimeline”分享到朋友圈，“WXSceneFavorite”分享到微信收藏     
					type: this.shareType,
					success: (e) => {
						console.log('success', e);
						uni.showModal({
							content: '分享成功',
							showCancel: false
						})
					},
					fail: (e) => {
						console.log('fail', JSON.stringify(e))
						uni.showModal({
							content: e.errMsg,
							showCancel: false
						})
					},
					complete: function() {
						console.log('分享操作结束!')
					}
				}

				switch (this.shareType) {
					case 0:
						shareOPtions.summary = this.shareText;
						shareOPtions.imageUrl = this.image;
						shareOPtions.title = '欢迎体验uniapp';
						shareOPtions.href = 'https://uniapp.dcloud.io';
						break;
					case 1:
						shareOPtions.summary = this.shareText;
						break;
					case 2:
						shareOPtions.imageUrl = this.image;
						break;
					case 5:
						shareOPtions.imageUrl = this.image ? this.image :
							'https://img-cdn-qiniu.dcloud.net.cn/uniapp/app/share-logo@3.png'
						shareOPtions.title = '欢迎体验uniapp';
						shareOPtions.miniProgram = {
							id: 'gh_33446d7f7a26',
							path: '/pages/tabBar/component/component',
							webUrl: 'https://uniapp.dcloud.io',
							type: 0
						};
						break;
					default:
						break;
				}

				if (shareOPtions.type === 0 && plus.os.name === 'iOS') { //如果是图文分享，且是ios平台，则压缩图片 
					shareOPtions.imageUrl = await this.compress();
				}
				if (shareOPtions.type === 1 && shareOPtions.provider === 'qq') { //如果是分享文字到qq，则必须加上href和title
					shareOPtions.href = 'https://uniapp.dcloud.io';
					shareOPtions.title = '欢迎体验uniapp';
				}
				uni.share(shareOPtions);
			},
			compress() { //压缩图片 图文分享要求分享图片大小不能超过20Kb
				console.log('开始压缩');
				let img = this.image;
				return new Promise((res) => {
					var localPath = plus.io.convertAbsoluteFileSystem(img.replace('file://', ''));
					console.log('after' + localPath);
					// 压缩size
					plus.io.resolveLocalFileSystemURL(localPath, (entry) => {
						entry.file((file) => { // 可通过entry对象操作图片 
							console.log('getFile:' + JSON.stringify(file));
							if (file.size > 20480) { // 压缩后size 大于20Kb
								plus.zip.compressImage({
									src: img,
									dst: img.replace('.jpg', '2222.jpg').replace('.JPG', '2222.JPG'),
									width: '10%',
									height: '10%',
									quality: 1,
									overwrite: true
								}, (event) => {
									console.log('success zip****' + event.size);
									let newImg = img.replace('.jpg', '2222.jpg').replace('.JPG', '2222.JPG');
									res(newImg);
								}, function(error) {
									uni.showModal({
										content: '分享图片太大,需要请重新选择图片!',
										showCancel: false
									})
								});
							}
						});
					}, (e) => {
						console.log('Resolve file URL failed: ' + e.message);
						uni.showModal({
							content: '分享图片太大,需要请重新选择图片!',
							showCancel: false
						})
					});
				})
			}

		}
	}
</script>

<style>
	/* 分享到 */
	.more-share-model {
		position: fixed;
		left: 0;
		top: 0;
		right: 0;
		bottom: 0;
		z-index: 100;
		background: rgba(51, 51, 51, 0.49);
	}

	.more-share {
		position: fixed;
		bottom: 0;
		z-index: 101;
		left: 0;
		right: 0;
		background-color: #FFFFFF
	}

	.more-share-title,
	.more-share-bottom {
		padding: 20upx;
		font-size: 32upx;
	}

	.more-share-body {
		white-space: nowrap;
		width: 100%;
		border-bottom: 1px solid #CCCCCC;
		height: 200upx;
		line-height: 200upx;
	}

	.more-share-item {
		width: 25%;
		display: inline-flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		height: 100%;
	}

	.more-share-hove {
		background: #eee;
	}

	.more-share-item>view:first-child {
		width: 100upx;
		height: 100upx;
		font-size: 55upx;
		text-align: center;
		border-radius: 100%;
		border: 1px solid #CCCCCC;
		color: #FFFFFF;
	}

	.more-share-item>view:last-child {
		color: #7A7A7A;
	}

	.more-share-weixin {
		background: #2AD198;
	}

	.more-share-pyq {
		background: #514D4C;
	}

	.more-share-weibo {
		background: #EE5E5E;
	}

	.more-share-qq {
		background: #4A73BA;
	}
</style>
