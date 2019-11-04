<template>
	<view>
		<uni-status-bar backgroundColor="#FFE933">
		</uni-status-bar>
		<!-- 引入背景图 -->
		<view class="icon iconfont icon-guanbi closeBtn " @tap="goBack"></view>
		<image class="logoBg" src="../../../static/common/loginhead.png" mode="widthFix" lazy-load> </image>
		<view class="body">
			<!-- 账号登录 -->
			<view class="body-input-main" v-if="!loginPhone">
				<input type="text" v-model="username" class="uni-input" placeholder="请输入账号" />
				<view class="input_wrap">
					<input type="text" v-model="password" class="uni-input" style="padding-right: 180upx;" placeholder="请输入密码" />
					<view class="forget">忘记密码？</view>
				</view>
			</view>
			<!-- 手机号登录 -->
			<view class="body-input-main" v-else>
				<view class="input_wrap">
					<view class="prefixNum">+86</view>
					<input type="text" v-model="phone" class="uni-input" style="padding-left: 90upx;" placeholder="请输入密码" />
				</view>
				<view class="input_wrap">
					<input type="text" v-model="code" class="uni-input" style="padding-right: 190upx;" placeholder="请输入验证码" />
					<view class="CodeBtn" @tap="getCode">{{codeNum === 0? '获取认证码' : "请" + codeNum + 's重新获取'}}</view>
				</view>
			</view>
		</view>
		<view style="padding: 20upx;">
			<button @tap="submit" :loading="loading" class="user-set-btn" :class="{'user-set-btn-disable':disable}" :disabled="disable">登录</button>
		</view>
		<!-- 切换登录方式 -->
		<view class="u-f-aj login-head" @tap="changeLogin"> {{!loginPhone ? '验证码登录' : '账号密码登录'}}<view class="icon iconfont icon-jinru"></view>
		</view>
		<!-- 第三方登录 -->
		<view class="other-login">
			<view class="u-f-aj login-head other-login-header">
				第三方登录
			</view>
			<other-login></other-login>
			<!-- 协议 -->
			<view class="login-rule u-f-aj login-head">注册及代表您同意<view class="rule">《xxxxxxx》</view>
			</view>
		</view>
	</view>
	</view>
</template>

<script>
	import uniStatusBar from '../../../components/uni-status-bar/uni-status-bar.vue';
	import otherLogin from '../../../components/home/other-login.vue'
	export default {
		components: {
			uniStatusBar,
			otherLogin
		},
		data() {
			return {
				loginPhone:false,
				disable: true,
				codeNum:0,
				username: "",
				phone:"",
				code:"",
				password: "",
				loading: false
			}
		},
		watch: {
			username(val) {
				this.change()
			},
			password(val) {
				this.change()
			},
			phone(val) {
				this.change()
			},
			code(val) {
				this.change()
			},
		},
		methods: {
			//返回上一页
			goBack() {
				uni.navigateBack({
					delta: 1
				})
			},
			//切换登录
			changeLogin(){
				this.initForm()
				this.loginPhone = !this.loginPhone;
			},
			//获取验证码
			getCode(){
				if(this.codeNum > 0) {
					uni.showToast({
						title:"不能重复获取",
						icon:"none"
					})
					return false;
				}else{
					this.codeNum = 5;
					let timer = setInterval(() => {
						this.codeNum--;
						if(this.codeNum < 1){
							console.log(this.codeNum)
							clearInterval(timer)
							this.codeNum = 0;
						}
					},1000)
				}
			},
			//提交
			submit() {
				if(!this.check()){return;}
				console.log("提交登录")
			},
			//初始化表单
			initForm(){
				this.password=""
				this.username=""
				this.code=""
				this.phone=""
			},
			//检测数据变化
			change() {
				if (this.username && this.password) {
					this.disable = false;
					return;
				}
				if (this.phone && this.code) {
					this.disable = false;
					return;
				}
				return true;
			},
			//数据验证 
			check() {
				if(this.loginPhone){
					if (!this.code || this.code == '') {
						uni.showToast({
							title: "验证码能为空",
							icon: "none"
						})
						return false;
					}
					if (!this.phone || this.phone == '') {
						uni.showToast({
							title: "手机号不能为空",
							icon: "none"
						})
						return false;
					}
					return true;
				}else{
					if (!this.username || this.username == '') {
						uni.showToast({
							title: "用户名不能为空",
							icon: "none"
						})
						return false;
					}
					if (!this.password || this.password == '') {
						uni.showToast({
							title: "密码不能为空",
							icon: "none"
						})
						return false;
					}
					return true;
				}
			
			},

		}
	}
</script>

<style>
	@import url("../../../common/form.css");

	.logoBg {
		width: 100%;
	}

	.login-head {
		padding: 10upx 0;
		color: #9E9E9E;
	}

	.other-login-header {
		position: relative;
	}

	.other-login-header:after,
	.other-login-header:before {
		position: absolute;
		content: "";
		height: 1upx;
		width: 100upx;
		top: 50%;
		background: #9E9E9E;
	}

	.rule {
		color: #2CAEFC;
	}

	.input_wrap {
		position: relative;
	}

	.forget {
		position: absolute;
		bottom: 15upx;
		right: 30upx;
	}
	.prefixNum{
		position: absolute;
		top: 15upx;
		color: #000000;
		left: 30upx;
	}
	.CodeBtn{
		position: absolute;
		padding: 0 10upx;
		background: #F4F4F4;
		color: #909090;
		bottom: 15upx;
		right: 30upx;
	}
	.other-login-header:after {
		left: 20%;
	}

	.other-login-header:before {
		right: 20%;
	}

	.closeBtn {
		position: fixed;
		top: 60upx;
		left: 30upx;
		font-size: 44upx;
		font-weight: bold;
		color: #332F0A;
	}
</style>
