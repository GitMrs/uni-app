<template>
	<view>
		<TabBar :currentIndex="currentIndex" @changeTab="changeTab" :tabBars="tabBar" />
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:swiperHeight + 'px'}" :current="currentIndex" @change="changeSwiper" >
				<swiper-item v-for="(items,index) in newsList" :key="index">
					<scroll-view class="list" scroll-y @scrolltolower="loadMore(index)">
						<template v-if="items.list.length > 0">
							<block v-for="(item,index_list) in items.list" :key="index_list">
								<topicList :item="item" :index="index_list"  />
							</block>
							<LoadMore :loadText="items.loadText" />
						</template>
						<!-- 无内容页 -->
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
	import TabBar from '../../components/tab-bar.vue';
	import LoadMore from '../../components/commom/load-more.vue';
	import Nothing from "../../components/commom/nothing.vue";
	import topicList from "../../components/topic-list.vue";
	export default {
		components: {
			TabBar,
			LoadMore,
			Nothing,
			topicList
		},
		data() {
			return {
				currentIndex: 0,
				swiperHeight: '500',
				newsList: [{
						loadText: "上拉加载更多",
						list: [{
							titlepic: "../../static/demo10.jpg",
							title: "话题名称",
							desc: "我是话题描述",
							totalnum: "100",
							todayNum: '10'
						},
						{
							titlepic: "../../static/demo10.jpg",
							title: "话题名称",
							desc: "我是话题描述",
							totalnum: "100",
							todayNum: '10'
						}, {
							titlepic: "../../static/demo10.jpg",
							title: "话题名称",
							desc: "我是话题描述",
							totalnum: "100",
							todayNum: '10'
						},
						{
							titlepic: "../../static/demo10.jpg",
							title: "话题名称",
							desc: "我是话题描述",
							totalnum: "100",
							todayNum: '10'
						},
						{
							titlepic: "../../static/demo10.jpg",
							title: "话题名称",
							desc: "我是话题描述",
							totalnum: "100",
							todayNum: '10'
						}, {
							titlepic: "../../static/demo10.jpg",
							title: "话题名称",
							desc: "我是话题描述",
							totalnum: "100",
							todayNum: '10'
						},
					]
					},
					{
						loadText: "上拉加载更多",
						list: []
					},
					{
						loadText: "上拉加载更多",
						list: []
					},
					{
						loadText: "上拉加载更多",
						list: []
					},
					{
						loadText: "上拉加载更多",
						list: []			
					},
					{
						loadText: "上拉加载更多",
						list: []		
					},
					{
						loadText: "上拉加载更多",
						list: []
					}
				],
				tabBar: [{
						name: "关注"
					},
					{
						name: "推荐"
					},
					{
						name: "体育"
					},
					{
						name: "热点"
					},
					{
						name: '财经'
					},
					{
						name: "娱乐"
					},
					{
						name: '其他'
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
		methods: {
			//上拉加载更多
			loadMore(index) {
				console.log("11")
				if (this.newsList[index].loadText != '上拉加载更多') {
					return
				}
				this.newsList[index].loadText = "加载中。。。。"
				setTimeout(() => {
					//加载完成
					let obj = {
							titlepic: "../../static/demo10.jpg",
							title: "话题名称",
							desc: "我是话题描述",
							totalnum: "100",
							todayNum: '10'
						}
					this.newsList[index].list.push(obj)
					this.newsList[index].loadText = "上拉加载更多"
				}, 1000)



				// this.newsList[index].loadText = "没有数据了"
			},
			//切换tab
			changeTab(index) {
				this.currentIndex = index
			},
			//切换swiper
			changeSwiper(e) {
				this.currentIndex = e.detail.current;
			}
		},
		
	}
</script>

<style>

</style>
