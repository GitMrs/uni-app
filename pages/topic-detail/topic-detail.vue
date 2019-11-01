<template>
	<view>
		<!-- 话题介绍 -->
		<topicInfo :item="topicInfo" />
		<!-- tab切换 -->
		<SwiperTabBar :currentIndex="currentIndex" @changeTab="changeTab" :tabBars="tabBar" scrollItemStyle="width:50%"
		 scrollStyle="border-bottom:0px" />
		<!-- 列表 -->
		<view class="topic-detail-list">
			<block v-for="(items,index) in tablist" :key="index">
				<template v-if="currentIndex == index">
					<block v-for="(item,index_list) in items.list" :key="index_list">
						<commomList :item="item" :index="index_list" />
					</block>
					<load-more :loadText="items.loadText" />
				</template>
			</block>
		</view>

	</view>
</template>

<script>
	import topicInfo from "../../components/topic-info.vue";
	import SwiperTabBar from "../../components/tab-bar.vue";
	import LoadMore from "../../components/commom/load-more.vue";
	import commomList from "../../components/common-list.vue"
	export default {
		components: {
			topicInfo,
			SwiperTabBar,
			LoadMore,
			commomList
		},
		data() {
			return {
				currentIndex: 0,
				swiperHeight: 500,
				topicInfo: {
					titlepic: "../../static/topicpic/11.jpeg",
					title: "记往事，敬余生",
					totalnum: '1000',
					todaynum: '1000',
					desc: "我是描述"
				},
				tabBar: [{
						name: '默认'
					},
					{
						name: '最新'
					}
				],
				tablist: [{
						loadText: "上拉加载更多",
						list: [{
								userpic: "../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "图文",
								type: 0, //0 为文字，1 为图文，2 为视频 3，分享
								img: true,
								titlepic: "../../static/datapic/22.jpg",
								video: false,
								share: false,
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							},
							{
								userpic: "../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "图文",
								type: 1,
								img: true,
								titlepic: "../../static/datapic/22.jpg",
								video: false,
								share: false,
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							},

							{
								userpic: "../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "图文",
								type: 1,
								img: true,
								titlepic: "../../static/datapic/22.jpg",
								video: false,
								share: false,
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							},
							{
								userpic: "../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								type: 2,
								title: "视频",
								titlepic: "../../static/datapic/22.jpg",
								video: {
									lonknum: '20w',
									long: "2:47"
								},
								share: false,
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							},
							{
								userpic: "../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "分享页",
								type: 3,
								video: false,
								share: {
									title: "分享",
									pic: "../../static/datapic/22.jpg"
								},
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							}
						]

					},
					{
						loadText: "上拉加载更多",
						list: [{
								userpic: "../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "图文",
								type: 0, //0 为文字，1 为图文，2 为视频 3，分享
								img: true,
								titlepic: "../../static/datapic/22.jpg",
								video: false,
								share: false,
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							},
							{
								userpic: "../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "图文",
								type: 1,
								img: true,
								titlepic: "../../static/datapic/22.jpg",
								video: false,
								share: false,
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							},

							{
								userpic: "../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "图文",
								type: 1,
								img: true,
								titlepic: "../../static/datapic/22.jpg",
								video: false,
								share: false,
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							},
							{
								userpic: "../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								type: 2,
								title: "视频",
								titlepic: "../../static/datapic/22.jpg",
								video: {
									lonknum: '20w',
									long: "2:47"
								},
								share: false,
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							},
							{
								userpic: "../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "分享页",
								type: 3,
								video: false,
								share: {
									title: "分享",
									pic: "../../static/datapic/22.jpg"
								},
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							}
						]
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
		// 上拉触底加载
		onReachBottom() {
			this.loadMore(this.currentIndex)
		},
		//下来刷新事件
		onPullDownRefresh() {
			this.getData();
		},
		methods: {
			//获取数据
			getData() {
				let arr = [{
						userpic: "../../static/topicpic/5.jpeg",
						username: "昵称",
						sex: 1, // 0 男，1女
						age: '25',
						isguanzhu: false,
						title: "图文",
						type: 0, //0 为文字，1 为图文，2 为视频 3，分享
						img: true,
						titlepic: "../../static/datapic/22.jpg",
						video: false,
						share: false,
						addree: "	深圳 龙岗",
						sharenum: 20,
						commentnum: 30,
						goodnum: 20
					},
					{
						userpic: "../../static/topicpic/1.jpeg",
						username: "昵称",
						sex: 0, // 0 男，1女
						age: '25',
						isguanzhu: false,
						title: "图文",
						type: 1,
						img: true,
						titlepic: "../../static/datapic/22.jpg",
						video: false,
						share: false,
						addree: "	深圳 龙岗",
						sharenum: 20,
						commentnum: 30,
						goodnum: 20
					},
				]
				setTimeout(() => {
					this.tablist[this.currentIndex].list = arr;
					uni.stopPullDownRefresh()
				}, 2000)
			},
			changeTab(index) {
				this.currentIndex = index
			},
			changeSwiper(e) {
				this.currentIndex = e.detail.current;
			},
			//上拉加载更多
			loadMore(index) {
				if (this.tablist[index].loadText != '上拉加载更多') {
					return
				}
				this.tablist[index].loadText = "加载中。。。。"
				setTimeout(() => {
					//加载完成
					let obj = {
						userpic: "../../static/topicpic/4.jpeg",
						username: "昵称",
						sex: 1, // 0 男，1女
						age: '25',
						isguanzhu: false,
						title: "图文",
						type: 1,
						img: true,
						titlepic: "../../static/datapic/22.jpg",
						video: false,
						share: false,
						addree: "	深圳 龙岗",
						sharenum: 20,
						commentnum: 30,
						goodnum: 20
					}

					this.tablist[index].list.push(obj)

					this.tablist[index].loadText = "上拉加载更多"
				}, 1000)
				// this.guanzhu.loadText = "没有数据了"
			},

		}
	}
</script>

<style>

</style>
