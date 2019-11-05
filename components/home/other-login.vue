<template>
	<view class="">
		<view class="other-login u-f-aj">
			<block v-for="(item,index) in providerList" :key="index">
				<view class="u-f-aj" @click="tologin(item)">
					<view class="icon iconfont" :class="['icon-' + item.zIcon]"></view>
				</view>
			</block>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				providerList: []
			}
		},
		methods: {
			goLogin() {
				uni.navigateTo({
					url: "../../pages/home/home-login/home-login"
				})
			},
			tologin(provider) {
				uni.login({
					provider: provider.id,
					// #ifdef MP-ALIPAY
					scopes: 'auth_user', //支付宝小程序需设置授权类型
					// #endif
					success: (res) => {
						console.log('login success:', res);
						// 更新保存在 store 中的登录状态
						// this.login(provider.id);
					},
					fail: (err) => {
						console.log('login fail:', err);
					}
				});
			}
		},
		mounted() {
			uni.getProvider({
				service: 'oauth',
				success: (result) => {
					this.providerList = result.provider.map((value) => {
						let providerName = '';
						let zIcon = '';
						switch (value) {
							case 'weixin':
								providerName = '微信登录'
								zIcon = 'weixin'
								break;
							case 'qq':
								providerName = 'QQ登录'
								zIcon = 'QQ'
								break;
							case 'sinaweibo':
								providerName = '新浪微博登录'
								zIcon = 'xinlangweibo'
								break;
								// case 'xiaomi':
								// 	providerName = '小米登录'
								// 	break;
								// case 'alipay':
								// 	providerName = '支付宝登录'
								// 	break;
								// case 'baidu':
								// 	providerName = '百度登录'
								// 	break;
								// case 'toutiao':
								// 	providerName = '头条登录'
								// 	break;
						}
						return {
							name: providerName,
							id: value,
							zIcon,
						}
					});

				},
				fail: (error) => {
					console.log('获取登录通道失败', error);
				}
			});
		},

	}
</script>

<style scoped>
	.other-login {
		padding: 20upx;
	}

	.other-login>view {
		flex: 1;
	}

	.other-login>view>view {
		width: 100upx;
		height: 100upx;
		border-radius: 100%;
		font-size: 44upx;
		color: #FFFFFF;
		text-align: center;
		line-height: 100upx;
		border: 1px solid;
	}

	.other-login .icon-QQ {
		background: #2CAEFC;
	}

	.other-login .icon-weixin {
		background: #2AD198;
	}

	.other-login .icon-xinlangweibo {
		background: #FC7729;
	}
</style>
