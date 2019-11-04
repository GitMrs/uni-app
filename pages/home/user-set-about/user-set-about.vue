<template>
	<view>
		<view class="top u-f-aj">
			<image src="../../../static/common/logo.png" mode="widthFix" lazy-load></image>
			<view class="">version1.0.0</view>
		</view>
		<view>
			<block v-for="(item,index) in list" :key="index">
				<home-list :item="item" :index="index"></home-list>
			</block>
		</view>
	</view>
</template>

<script>
	import homeList from '../../../components/commom/home-list.vue';
	export default {
		components: {
			homeList
		},
		data() {
			return {
				list: [{
						name: '新版本检测',
						clicktype: "",
						url: ''
					},
					{
						name: '用户协议',
						clicktype: "",
						url: ''
					}
				]
			}
		},
		methods: {

		}
	}
</script>

<style>
	@import url("../../../common/form.css");

	.top {
		flex-direction: column;
		margin-top: 30upx;
		margin-bottom: 60upx;
	}

	.top image {
		width: 80%;
	}

	.top>view {
		color: #989898;
	}

	.home-list {
		padding: 20px;
	}
</style>
