<template>
	<view>
		<TabBar :currentIndex="currentIndex" @changeTab="changeTab" :tabBars="tabBar" />
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:swiperHeight + 'px'}" :current="currentIndex" @change="changeSwiper" >
				<swiper-item v-for="(items,index) in newsList" :key="index">
					<scroll-view class="list" scroll-y @scrolltolower="loadMore(index)">
						<template v-if="items.list.length > 0">
							<block v-for="(item,index_list) in items.list" :key="index_list">
								<IndexList :item="item" :index="index_list" />
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
	import IndexList from "../../components/index-list.vue";
	import TabBar from '../../components/tab-bar.vue';
	import LoadMore from '../../components/commom/load-more.vue';
	import Nothing from "../../components/commom/nothing.vue"
	export default {
		data() {
			return {
				currentIndex: 0,
				swiperHeight: '500',
				newsList: [{
						loadText: "上拉加载更多",
						list: [{
								userpic: "../../static/topicpic/9.jpeg",
								username: "昵称",
								isguanzhu: false,
								title: "信息1",
								type: "img",
								titlepic: "../../static/datapic/1.jpg",
								infonum: {
									index: 1, //0代表没有操作，1：顶。2：踩
									ding: 11,
									cai: 12,
								},
								comment: 10,
								share: 10
							},
							{
								userpic: "../../static/topicpic/9.jpeg",
								username: "昵称",
								isguanzhu: true,
								title: "信息1",
								type: "video",
								titlepic: "../../static/datapic/1.jpg",
								playnum: "20w",
								long: "2:57",
								infonum: {
									index: 0, //0代表没有操作，1：顶。2：踩
									ding: 11,
									cai: 12,
								},
								comment: 10,
								share: 10
							}
						]
					},
					{
						loadText: "上拉加载更多",
						list: [{
								userpic: "../../static/topicpic/9.jpeg",
								username: "昵称",
								isguanzhu: true,
								title: "信息1",
								type: "img",
								titlepic: "../../static/datapic/1.jpg",
								infonum: {
									index: 1, //0代表没有操作，1：顶。2：踩
									ding: 11,
									cai: 12,
								},
								comment: 10,
								share: 10
							},
							{
								userpic: "../../static/topicpic/9.jpeg",
								username: "昵称",
								isguanzhu: true,
								title: "信息1",
								type: "video",
								titlepic: "../../static/datapic/1.jpg",
								playnum: "20w",
								long: "2:57",
								infonum: {
									index: 0, //0代表没有操作，1：顶。2：踩
									ding: 11,
									cai: 12,
								},
								comment: 10,
								share: 10
							}
						]

					},
					{
						loadText: "上拉加载更多",
						list: []
					},
					{
						loadText: "上拉加载更多",
						list: [{
								userpic: "../../static/topicpic/9.jpeg",
								username: "昵称",
								isguanzhu: true,
								title: "信息1",
								type: "img",
								titlepic: "../../static/datapic/1.jpg",
								infonum: {
									index: 1, //0代表没有操作，1：顶。2：踩
									ding: 11,
									cai: 12,
								},
								comment: 10,
								share: 10
							},
							{
								userpic: "../../static/topicpic/9.jpeg",
								username: "昵称",
								isguanzhu: true,
								title: "信息1",
								type: "video",
								titlepic: "../../static/datapic/1.jpg",
								playnum: "20w",
								long: "2:57",
								infonum: {
									index: 0, //0代表没有操作，1：顶。2：踩
									ding: 11,
									cai: 12,
								},
								comment: 10,
								share: 10
							}
						]

					},
					{
						loadText: "上拉加载更多",
						list: [{
								userpic: "../../static/topicpic/9.jpeg",
								username: "昵称",
								isguanzhu: true,
								title: "信息1",
								type: "img",
								titlepic: "../../static/datapic/1.jpg",
								infonum: {
									index: 1, //0代表没有操作，1：顶。2：踩
									ding: 11,
									cai: 12,
								},
								comment: 10,
								share: 10
							},
							{
								userpic: "../../static/topicpic/9.jpeg",
								username: "昵称",
								isguanzhu: true,
								title: "信息1",
								type: "video",
								titlepic: "../../static/datapic/1.jpg",
								playnum: "20w",
								long: "2:57",
								infonum: {
									index: 0, //0代表没有操作，1：顶。2：踩
									ding: 11,
									cai: 12,
								},
								comment: 10,
								share: 10
							}
						]

					},
					{
						loadText: "上拉加载更多",
						list: [{
								userpic: "../../static/topicpic/9.jpeg",
								username: "昵称",
								isguanzhu: true,
								title: "信息1",
								type: "img",
								titlepic: "../../static/datapic/1.jpg",
								infonum: {
									index: 1, //0代表没有操作，1：顶。2：踩
									ding: 11,
									cai: 12,
								},
								comment: 10,
								share: 10
							},
							{
								userpic: "../../static/topicpic/9.jpeg",
								username: "昵称",
								isguanzhu: true,
								title: "信息1",
								type: "video",
								titlepic: "../../static/datapic/1.jpg",
								playnum: "20w",
								long: "2:57",
								infonum: {
									index: 0, //0代表没有操作，1：顶。2：踩
									ding: 11,
									cai: 12,
								},
								comment: 10,
								share: 10
							}
						]

					},
					{
						loadText: "上拉加载更多",
						list: [{
								userpic: "../../static/topicpic/9.jpeg",
								username: "昵称",
								isguanzhu: true,
								title: "信息1",
								type: "img",
								titlepic: "../../static/datapic/1.jpg",
								infonum: {
									index: 1, //0代表没有操作，1：顶。2：踩
									ding: 11,
									cai: 12,
								},
								comment: 10,
								share: 10
							},
							{
								userpic: "../../static/topicpic/9.jpeg",
								username: "昵称",
								isguanzhu: true,
								title: "信息1",
								type: "video",
								titlepic: "../../static/datapic/1.jpg",
								playnum: "20w",
								long: "2:57",
								infonum: {
									index: 0, //0代表没有操作，1：顶。2：踩
									ding: 11,
									cai: 12,
								},
								comment: 10,
								share: 10
							}
						]

					}
				],
				list: [{
						userpic: "../../static/topicpic/9.jpeg",
						username: "昵称",
						isguanzhu: true,
						title: "信息1",
						type: "img",
						titlepic: "../../static/datapic/1.jpg",
						infonum: {
							index: 1, //0代表没有操作，1：顶。2：踩
							ding: 11,
							cai: 12,
						},
						comment: 10,
						share: 10
					},
					{
						userpic: "../../static/topicpic/9.jpeg",
						username: "昵称",
						isguanzhu: true,
						title: "信息1",
						type: "video",
						titlepic: "../../static/datapic/1.jpg",
						playnum: "20w",
						long: "2:57",
						infonum: {
							index: 0, //0代表没有操作，1：顶。2：踩
							ding: 11,
							cai: 12,
						},
						comment: 10,
						share: 10
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
		onNavigationBarSearchInputClicked() {
			// 路由跳转
			uni.navigateTo({
				url:"../search/search"
			})
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
			loadMore(index){
				if(this.newsList[index].loadText != '上拉加载更多') {return}
					this.newsList[index].loadText = "加载中。。。。"
				setTimeout(() => {
					//加载完成
					let obj = {
								userpic: "../../static/topicpic/9.jpeg",
								username: "昵称",
								isguanzhu: true,
								title: "信息1",
								type: "img",
								titlepic: "../../static/datapic/1.jpg",
								infonum: {
									index: 1, //0代表没有操作，1：顶。2：踩
									ding: 11,
									cai: 12,
								},
								comment: 10,
								share: 10
							}
							this.newsList[index].list.push(obj)
						this.newsList[index].loadText = "上拉加载更多"
				},1000)
				
			
			
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
		components: {
			IndexList,
			TabBar,
			LoadMore,
			Nothing
		}
	}
</script>

<style>

</style>
