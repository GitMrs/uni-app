<template>
	<view>
		<!-- home -->
		<template v-if="!isLogin">
			<otherLogin />
		</template>
		<template v-else="isLogin">
			<loginInfo :info="useInfo" />
		</template>
		<!-- 数据 -->
		<homeDate :homeData="totalNum" />
		<!-- 广告为 -->
		<view class="hot-img u-f-aj">
			<image src="../../static/datapic/16.jpg" mode="widthFix" lazy-load></image>
		</view>
		<!-- 功能列表 -->
		<view class="home-list">
			<block v-for="(item,index) in list" :key="index">
				<home-list :item="item" :index="index"></home-list>
			</block>
		</view>
	</view>
</template>

<script>
	import homeList from "../../components/commom/home-list.vue";
	import loginInfo from '../../components/home/login-info.vue';
	import otherLogin from "../../components/home/other-login.vue"
	import homeDate from '../../components/home/home-data.vue'
	export default {
		components: {
			homeList,
			otherLogin,
			loginInfo,
			homeDate
		},
		data() {
			return {
				isLogin: true,
				useInfo: {
					userpic: '../../static/topicpic/7.jpeg',
					username: '昵称',
					totalnum: '100',
					todaynum: 0
				},
				totalNum: [{
						name: '糗事',
						num: 0
					},
					{
						name: '动态',
						num: 0
					},
					{
						name: '评论',
						num: 0
					},
					{
						name: '收藏',
						num: 0
					},
				],
				list: [{
						name: '浏览记录',
						icon: 'liulan',
						clicktype:"",
						url:''
					},
					{
						name: '糗百认证',
						icon: 'huiyuanvip',
						clicktype:'',
						url:''
					},
					{
						name: '审核认证',
						icon: 'keyboard',
						clicktype:'',
						url:''
					},
				]
			}
		},
		onNavigationBarButtonTap(e) {
			e.index === 0 && console.log('点击了menu图标')
		},
		methods: {

		}
	}
</script>

<style>
	.hot-img {
		padding: 20upx;
	}

	.hot-img image {
		width: 100%;
		height: 100upx;
		border-radius: 10upx;
	}

	.home-list {
		padding: 20px;
	}
</style>
