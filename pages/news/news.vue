<template>
	<view>
		<newsTabBar :tabBars="tabBars" :tabIndex="tabIndex" @change-tab-index="changeTab" />

		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:swiperHeight + 'px'}" :current="tabIndex" @change="changeSwiper">
				<!-- 关注 -->
				<swiper-item>
					<scroll-view class="list" scroll-y @scrolltolower="loadMore(0)">
						<block v-for="(item,index) in guanzhu.list" :key="index">
							<commomList :item="item" :index="index"></commomList>
						</block>
						<LoadMore :loadText="guanzhu.loadText" />
					</scroll-view>
				</swiper-item>
				<!-- 话题 -->
				<swiper-item>
					<scroll-view class="list" scroll-y @scrolltolower="loadMore(1)">
						<!-- 搜索 -->
						<view class="search-input">
							<input type="text" value="" class="uni-input" placeholder="搜索内容" placeholder-class="topic-search icon iconfont icon-sousuo" />
						</view>
						<!-- 轮播图 -->
						<swiper class="topic-swiper" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
							<swiper-item v-for="(item,index) in topic.swiper" :key="index">
								<image :src="item.src" mode="widthFix" lazy-load></image>
							</swiper-item>
						</swiper>

						<!-- 热门分类 -->
						<TopicNav :topicNav="topic.nav" />
						<!-- 最近更新 -->
						<view class="topic-new">
							<view>最近更新</view>
							<block v-for="(item,index) in huati.list" :key="index">
								<topicList :item="item" :index="index" />
							</block>
							<LoadMore :loadText="huati.loadText"></LoadMore>
						</view>
					</scroll-view>

				</swiper-item>
			</swiper>
		</view>

	</view>
</template>

<script>
	import newsTabBar from "../../components/news-tab-bar.vue";
	import commomList from '../../components/common-list.vue';
	import LoadMore from "../../components/commom/load-more.vue";
	import TopicNav from "../../components/topic-nav.vue";
	import topicList from "../../components/topic-list.vue";
	export default {
		components: {
			newsTabBar,
			commomList,
			LoadMore,
			TopicNav,
			topicList
		},
		data() {
			return {
				tabIndex: 0,
				swiperHeight: 500,
				topic: {
					nav: [{
							name: "最新"
						},
						{
							name: "故事"
						},
						{
							name: "新闻"
						},
						{
							name: "时尚"
						},
						{
							name: "游戏"
						},
						{
							name: "打卡"
						}
					],
					swiper: [{
							src: "../../static/banner1.jpg",
						},
						{
							src: "../../static/banner2.jpg",
						},
						{
							src: "../../static/banner3.jpg",
						}
					]
				},

				tabBars: [{
						name: "关注"
					},
					{
						name: "话题"
					}
				],
				huati: {
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
						}, {
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
						}
					]
				},
				guanzhu: {
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
			changeTab(index) {
				this.tabIndex = index;
			},
			changeSwiper(e) {
				this.tabIndex = e.detail.current;
			},
			//上拉加载更多
			loadMore(type) {
				console.log(111)
				if (type === 0) {
					if (this.guanzhu.loadText != '上拉加载更多') {
						return
					}
					console.log("222")
					this.guanzhu.loadText = "加载中。。。。"
					setTimeout(() => {
						//加载完成
						let obj = {
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
						}
						this.guanzhu.list.push(obj)

						this.guanzhu.loadText = "上拉加载更多"
					}, 1000)

				} else {
					if (this.huati.loadText != '上拉加载更多') {
						return
					}
					console.log("222")
					this.huati.loadText = "加载中。。。。"
					setTimeout(() => {
						//加载完成
						let obj = {
							titlepic: "../../static/demo10.jpg",
							title: "话题名称",
							desc: "我是话题描述",
							totalnum: "100",
							todayNum: '10'
						}

						this.huati.list.push(obj)

						this.huati.loadText = "上拉加载更多"
					}, 1000)

				}

				// this.guanzhu.loadText = "没有数据了"
			},
		}
	}
</script>
<style>
	.search-input {
		padding: 20upx;
	}

	.search-input>input {
		background: #F4F4F4;
		border-radius: 10upx;
	}

	.topic-search {
		display: flex;
		justify-content: center;
		font-size: 28upx;
	}

	.topic-swiper {
		padding: 0 20upx 20upx;
		width: 100%;

	}

	.topic-swiper image {
		width: 100%;
		border-radius: 10upx;
	}

	.topic-new {
		padding: 20upx;

	}

	.topic-new>view {
		padding-bottom: 10upx;
		font-size: 32upx;
	}


</style>
