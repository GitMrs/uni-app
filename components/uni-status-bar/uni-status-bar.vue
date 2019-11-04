<template>
	<view :style="{ height: statusBarHeight, background:backgroundColor}" class="uni-status-bar">
		<slot />
	</view>
</template>

<script>
	var statusBarHeight = uni.getSystemInfoSync().statusBarHeight + 'px'
	export default {
		name: 'UniStatusBar',
		props:{
			backgroundColor:{
					type:String
			}
		},
		data() {
			return {
				statusBarHeight: statusBarHeight
			}
		}
	}
</script>

<style>
	.uni-status-bar {
		display: block;
		width: 100%;
		height: 20px;
		height: var(--status-bar-height);
	}
</style>