<template>
	<view>
		搜索页
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		//监听原生标题按钮事件
		onNavigationBarButtonTap(e) {
			if (e.index == 0) {
				//返回上级菜单
				uni.navigateBack({
					delta: 1
				})
			}
			console.log(e)
		},
		//	监听输入框输入事件
		onNavigationBarSearchInputChanged(e) {
			console.log(e.text)
		},
		//监听键盘搜索页面
		onNavigationBarSearchInputConfirmed() {
			console.log(e.text)
		},
		
		methods: {

		}
	}
</script>

<style>

</style>
