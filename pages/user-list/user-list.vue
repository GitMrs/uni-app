<template>
	<view>
		<!-- tab-bar 切换 -->
		<SwiperTabBar :currentIndex="currentIndex" @changeTab="changeTab" :tabBars="tabBar" scrollItemStyle="width:33.3%"
		 scrollStyle="border-bottom:0px" />
		<!-- 列表 -->
		<!-- <view class="user-list-wrap"> -->
			<block v-for="(item,index) in list" :key="index">
				<user-list :item="item" :index='index'></user-list>
			</block>
		
		<!-- </view> -->

	</view>
</template>

<script>
	import SwiperTabBar from '../../components/tab-bar.vue';
	import UserList from '../../components/user-list.vue';
	export default {
		components: {
			SwiperTabBar,
			UserList
		},
		data() {
			return {
				currentIndex: 0,
				list:[
					{
						userpic:"../../static/userpic/6.jpg",
						username:"昵称",
						sex:0,
						age:16,
						isguanzhu:false
					},
					{
						userpic:"../../static/userpic/6.jpg",
						username:"昵称",
						sex:1,
						age:16,
						isguanzhu:false
					},
					{
						userpic:"../../static/userpic/6.jpg",
						username:"昵称",
						sex:1,
						age:16,
						isguanzhu:false
					},
					{
						userpic:"../../static/userpic/6.jpg",
						username:"昵称",
						sex:1,
						age:16,
						isguanzhu:true
					}
				],
				tabBar: [{
						name: '互关',
						num: "10"
					},
					{
						name: "关注",
						num: "10"
					},
					{
						name: "粉丝",
						num: '10'
					}
				]
			}
		},
		//导航按钮
		onNavigationBarButtonTap(e) {
			if (e.index === 0) {
				uni.navigateBack({
					delta: 1
				})
			}
		},
		//原生搜索文字
		onNavigationBarSearchInputChanged(e) {

		},
		//键盘搜索按键
		onNavigationBarSearchInputConfirmed() {

		},
		methods: {
			changeTab(index) {
				this.currentIndex = index
			}
		}
	}
</script>

<style>
/* 	.user-list-wrap {
		padding: 20upx;
	} */

</style>
