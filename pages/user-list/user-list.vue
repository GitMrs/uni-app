<template>
	<view>
		<!-- tab-bar 切换 -->
		<SwiperTabBar :currentIndex="currentIndex" @changeTab="changeTab" :tabBars="tabBar" scrollItemStyle="width:33.3%"
		 scrollStyle="border-bottom:0px" />
		<!-- 列表 -->
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:swiperHeight + 'px'}" :current="currentIndex" @change="changeSwiper">
				<swiper-item v-for="(items,index) in tablist" :key="index">
					<scroll-view class="list" scroll-y @scrolltolower="loadMore(index)">
						<template v-if="items.list.length > 0">
							<block v-for="(item,index_list) in items.list" :key="index_list">
								<user-list :item="item" :index='index_list'></user-list>
							</block>
							<load-more :loadText="items.loadText" />
						</template>
						<template v-else>
							<Nothing />
						</template>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>

	</view>
</template>

<script>
	import SwiperTabBar from '../../components/tab-bar.vue';
	import UserList from '../../components/user-list.vue';
	import LoadMore from '../../components/commom/load-more.vue';
	import Nothing from "../../components/commom/nothing.vue";
	export default {
		components: {
			SwiperTabBar,
			UserList,
			LoadMore,
			Nothing
		},
		data() {
			return {
				currentIndex: 0,
				swiperHeight: 500,
				tablist: [{
						loadText: "上拉加载更多",
						list: [{
								userpic: "../../static/userpic/6.jpg",
								username: "昵称",
								sex: 0,
								age: 16,
								isguanzhu: false
							},
							{
								userpic: "../../static/userpic/6.jpg",
								username: "昵称",
								sex: 1,
								age: 16,
								isguanzhu: false
							},
							{
								userpic: "../../static/userpic/6.jpg",
								username: "昵称",
								sex: 1,
								age: 16,
								isguanzhu: false
							}, {
								userpic: "../../static/userpic/6.jpg",
								username: "昵称",
								sex: 1,
								age: 16,
								isguanzhu: false
							}, {
								userpic: "../../static/userpic/6.jpg",
								username: "昵称",
								sex: 1,
								age: 16,
								isguanzhu: false
							}, {
								userpic: "../../static/userpic/6.jpg",
								username: "昵称",
								sex: 1,
								age: 16,
								isguanzhu: false
							}, {
								userpic: "../../static/userpic/6.jpg",
								username: "昵称",
								sex: 1,
								age: 16,
								isguanzhu: false
							}, {
								userpic: "../../static/userpic/6.jpg",
								username: "昵称",
								sex: 1,
								age: 16,
								isguanzhu: false
							}, {
								userpic: "../../static/userpic/6.jpg",
								username: "昵称",
								sex: 1,
								age: 16,
								isguanzhu: false
							}, {
								userpic: "../../static/userpic/6.jpg",
								username: "昵称",
								sex: 1,
								age: 16,
								isguanzhu: false
							}, {
								userpic: "../../static/userpic/6.jpg",
								username: "昵称",
								sex: 1,
								age: 16,
								isguanzhu: false
							},
							{
								userpic: "../../static/userpic/6.jpg",
								username: "昵称",
								sex: 1,
								age: 16,
								isguanzhu: false
							},
							{
								userpic: "../../static/userpic/6.jpg",
								username: "昵称",
								sex: 1,
								age: 16,
								isguanzhu: true
							}
						]
					},
					{
						loadText: "没有更多的了",
						list: [{
								userpic: "../../static/userpic/1.jpg",
								username: "昵称",
								sex: 0,
								age: 16,
								isguanzhu: false
							},
							{
								userpic: "../../static/userpic/2.jpg",
								username: "昵称",
								sex: 1,
								age: 16,
								isguanzhu: false
							},
							{
								userpic: "../../static/userpic/3.jpg",
								username: "昵称",
								sex: 1,
								age: 16,
								isguanzhu: false
							},
							{
								userpic: "../../static/userpic/6.jpg",
								username: "昵称",
								sex: 1,
								age: 16,
								isguanzhu: true
							}
						]
					},
					{
						loadText: "上拉加载更多",
						list: []
					},
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
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					let height = res.windowHeight - uni.upx2px(100);
					this.swiperHeight = height;
					console.log(this.swiperHeight)

				}
			})
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
			},
			changeSwiper(e) {
				this.currentIndex = e.detail.current;
			},
			loadMore(index) {
				console.log(index)
				if (this.tablist[index].loadText != '上拉加载更多') {
					return
				}
				this.tablist[index].loadText = "加载中。。。。"
				setTimeout(() => {
					//加载完成
					let obj = {
						userpic: "../../static/userpic/6.jpg",
						username: "昵称",
						sex: 0,
						age: 16,
						isguanzhu: false
					}
					this.tablist[index].list.push(obj)

					this.tablist[index].loadText = "上拉加载更多"
				}, 1000)
				// this.guanzhu.loadText = "没有数据了"
			}
		}
	}
</script>

<style>
	/* 	.user-list-wrap {
		padding: 20upx;
	} */
</style>
