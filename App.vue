<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show1')
		},
		onHide: function() {
			console.log('App Hide2')
		}
	}
</script>

<style>
	/* uni.css - 通用组件、模板样式库，可以当作一套ui库应用 */
	@import './common/uni.css';
	/* 引入自定义图标库 */
	@import './common/font/iconfont.css';
	
	/* 引入动画库 */
	@import "./common/animate.css";
</style>
