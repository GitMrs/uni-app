<template>
	<view class="body">
		<input type="text" v-model="oldPassword" class="uni-input" placeholder="请输入旧密码" />
		<input type="text" v-model="newPassword" class="uni-input" placeholder="请输入新密码" />
		<input type="text" v-model="surePassword" class="uni-input" placeholder="请输入确认密码" />
		<view><button @tap="submit" :loading="loading" class="user-set-btn" :class="{'user-set-btn-disable':disable}" :disabled="disable">完成</button></view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				oldPassword: '',
				newPassword: '',
				surePassword: '',
				disable: true,
				loading: false,
			}
		},
		watch: {
			oldPassword(val) {
				this.change()
			},
			newPassword(val) {
				this.change()
			},
			surePassword(val) {
				this.change()
			}
		},
		methods: {
			change() {
				if (this.oldPassword && this.newPassword && this.surePassword) {
					console.log(111)
					this.disable = false;
					return;
				}
					console.log(1222)
				return true;
			},
			check() {
				if (!this.oldPassword || this.oldPassword == '') {
					uni.showToast({
						title: "旧密码不能为空",
						icon: "none"
					})
					return false;
				}
				if (!this.newPassword || this.newPassword == '') {
					uni.showToast({
						title: "新密码不能为空",
						icon: "none"
					})
					return false;
				}
				if (!this.surePassword || this.surePassword == '') {
					uni.showToast({
						title: "确认密码不能为空",
						icon: "none"
					})
					return false;
				}
				if (!this.surePassword !== this.newPassword) {
					uni.showToast({
						title: "确认密码和新密码不一致！",
						icon: "none"
					})
					return false;
				}
				// if(this.oldPassword && this.newPassword && this.surePassword && this.oldPassword!="" &&  this.newPassword != '' && this.oldPassword != ''){
				// 	return true
				// }
				// uni.showToast({
				// 	title:"请将数据填写完成",
				// 	icon:"none"
				// })
				return true;
			},
			submit() {
				this.loading = true
				if (!this.check()) {
					this.loading = false;
					return;

				}
				uni.showToast({
					title: '确认通过'
				});
				this.loading = false;
			}
		}
	}
</script>

<style>
	@import url("../../../common/form.css");
</style>
