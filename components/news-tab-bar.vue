<template>
	<view>
		<uni-nav-bar :border="false"  :fixed="true" :statusBar="true" @click-right="add">
			<!-- 左边 -->
			<block slot="left">
				<view class="nav-left">
					<view class="icon iconfont icon-qiandao"></view>
				</view>
			</block>
			<!-- 中间 -->
			<view class="u-f-aj nav-bar-bar">
				<block v-for="(item,index) in tabBars" :key="index">
					<view class="u-f-aj" @tap="changeTab(index)" :class="{active:tabIndex === index}">{{ item.name }}
						<view class="nav-tab-bar-line"></view>
					</view>
				</block>
			</view>
			<!-- 右边 -->
			<block slot="right">
				<view class="nav-right">
					<view class="icon iconfont icon-bianji"></view>
				</view>
			</block>
		</uni-nav-bar>
	</view>
</template>

<script>
	import uniNavBar from "./uni-nav-bar/uni-nav-bar.vue";
	export default {
		components:{
			uniNavBar
		},
		props:{
			tabBars:Array,
			tabIndex:Number
		},
		data() {
			return {

			};
		},
		methods: {
			changeTab(index) {
				this.$emit("change-tab-index",index)
			},
			add() {
				uni.navigateTo({
					url: "../add-up/add-up"
				})
			}
		}
	}
</script>

<style scoped>
	.nav-left,
	.nav-right {
	}

	.nav-left {
		margin-left: 30upx;
		color: #FF9619;
	}
	.nav-left>view{
		font-size: 40upx;
	}
	.nav-bar-bar {
		width: 100%;
		margin-left: 19upx;
		position: relative;
	}

	.nav-bar-bar view {
		padding: 0 15upx;
		font-size: 32upx;
		font-weight: bold;
		color: #969696;
	}

	.active {
		color: #333 !important;
	}

	.nav-tab-bar-line {
		border-bottom: 5upx solid #FEDE33;
		border-top: 5upx solid #FEDE33;
		width: 40upx;
		border-radius: 20upx;
		position: absolute;
		bottom: -3upx;
		display: none;
	}

	.active .nav-tab-bar-line {
		display: block;
	}
</style>
