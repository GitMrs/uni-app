<template>
	<view>
		<!-- 操作菜单 -->
		<userPopup :show="show" @hidePopup="hidePopup" @lahei="lahei" @beizhu="beizhu" />
		<!-- 上部信息 -->
		<userSpaceHead :item="userInfo" />
		<!-- 统计 -->
		<view class="user-space-desc">
			<home-data :homeData="usertotal"></home-data>
			<view style="height: 20upx;background: #F4F4F4;"></view>
		</view>
		<!-- tap导航 -->
		<TabBar :currentIndex="currentIndex" @changeTab="changeTab" :tabBars="tabBar" scrollItemStyle="width:33%" scrollStyle="border-bottom:0px"></TabBar>

		<!-- 列表 -->
		<view class="topic-detail-list">
			<block v-for="(items,index) in tablist" :key="index">
				<template v-if="currentIndex === 0">
					<!-- 主页 -->
					<view class="animated fadeInLeft ">
						<view class="user-space-info">
							<view class="user-space-item">
								<view class="">账号信息</view>
								<view class="">糗龄：150天</view>
								<view class="">糗百ID：1110001</view>
							</view>
						</view>
						<view class="user-space-info">
							<view class="user-space-item">
								<view class="">个人信息</view>
								<view class="">星座：天鸟座</view>
								<view class="">职业：IT</view>
								<view class="">故乡：天鸟星</view>
								<view class="">情感：未知</view>
							</view>
						</view>

					</view>
				</template>
				<template v-else-if="currentIndex == index ">
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
	import userSpaceHead from "../../../components/user-space/user-space-head.vue";
	import homeData from '../../../components/home/home-data.vue';
	import TabBar from "../../../components/tab-bar.vue";
	import LoadMore from "../../../components/commom/load-more.vue";
	import userPopup from '../../../components/user-space/user-popup.vue';
	import commomList from "../../../components/common-list.vue"
	export default {
		components: {
			userSpaceHead,
			homeData,
			LoadMore,
			commomList,
			TabBar,
			userPopup
		},
		data() {
			return {
				show:false,
				currentIndex: 0,
				tabBar: [{
						name: "主页"
					},
					{
						name: '糗事'
					},
					{
						name: '动态'
					}
				],
				tablist: [{
						loadText: "上拉加载更多",
						list: [{
								userpic: "../../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "图文",
								type: 0, //0 为文字，1 为图文，2 为视频 3，分享
								img: true,
								titlepic: "../../../static/datapic/22.jpg",
								video: false,
								share: false,
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							},
							{
								userpic: "../../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "图文",
								type: 1,
								img: true,
								titlepic: "../../../static/datapic/22.jpg",
								video: false,
								share: false,
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							},

							{
								userpic: "../../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "图文",
								type: 1,
								img: true,
								titlepic: "../../../static/datapic/22.jpg",
								video: false,
								share: false,
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							},
							{
								userpic: "../../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								type: 2,
								title: "视频",
								titlepic: "../../../static/datapic/22.jpg",
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
								userpic: "../../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "分享页",
								type: 3,
								video: false,
								share: {
									title: "分享",
									pic: "../../../static/datapic/22.jpg"
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
								userpic: "../../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "图文",
								type: 0, //0 为文字，1 为图文，2 为视频 3，分享
								img: true,
								titlepic: "../../../static/datapic/22.jpg",
								video: false,
								share: false,
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							},
							{
								userpic: "../../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "图文",
								type: 1,
								img: true,
								titlepic: "../../../static/datapic/22.jpg",
								video: false,
								share: false,
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							},

							{
								userpic: "../../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "图文",
								type: 1,
								img: true,
								titlepic: "../../../static/datapic/22.jpg",
								video: false,
								share: false,
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							},
							{
								userpic: "../../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								type: 2,
								title: "视频",
								titlepic: "../../../static/datapic/22.jpg",
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
								userpic: "../../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "分享页",
								type: 3,
								video: false,
								share: {
									title: "分享",
									pic: "../../../static/datapic/22.jpg"
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
								userpic: "../../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "图文",
								type: 0, //0 为文字，1 为图文，2 为视频 3，分享
								img: true,
								titlepic: "../../../static/datapic/22.jpg",
								video: false,
								share: false,
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							},
							{
								userpic: "../../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "图文",
								type: 1,
								img: true,
								titlepic: "../../../static/datapic/22.jpg",
								video: false,
								share: false,
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							},

							{
								userpic: "../../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "图文",
								type: 1,
								img: true,
								titlepic: "../../../static/datapic/22.jpg",
								video: false,
								share: false,
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							},
							{
								userpic: "../../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								type: 2,
								title: "视频",
								titlepic: "../../../static/datapic/22.jpg",
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
								userpic: "../../../static/topicpic/4.jpeg",
								username: "昵称",
								sex: 0, // 0 男，1女
								age: '25',
								isguanzhu: false,
								title: "分享页",
								type: 3,
								video: false,
								share: {
									title: "分享",
									pic: "../../../static/datapic/22.jpg"
								},
								addree: "	深圳 龙岗",
								sharenum: 20,
								commentnum: 30,
								goodnum: 20
							}
						]
					}
				],
				userInfo: {
					bg: '../../../static/datapic/26.jpg',
					username: '有丝分裂的草',
					sex: 0,
					age: '18',
					isguanzhu: true
				},
				usertotal: [{
						name: '获赞',
						num: '10k'
					},
					{
						name: "关注",
						num: '11',
					},
					{
						name: "粉丝",
						num: "12"
					}
				],

			}
		},
		onNavigationBarButtonTap(e) {
			e.index === 0 && this.openPopup()
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
			hidePopup(){
				this.show = false;
			},
			openPopup(){
				this.show = true;
			},
			//拉黑
			lahei(){},
			//备注
			beizhu(){},
			changeTab(index) {
				this.currentIndex = index
			},
			//获取数据
			getData() {
				let arr = [{
						userpic: "../../../static/topicpic/5.jpeg",
						username: "昵称",
						sex: 1, // 0 男，1女
						age: '25',
						isguanzhu: false,
						title: "图文",
						type: 0, //0 为文字，1 为图文，2 为视频 3，分享
						img: true,
						titlepic: "../../../static/datapic/22.jpg",
						video: false,
						share: false,
						addree: "	深圳 龙岗",
						sharenum: 20,
						commentnum: 30,
						goodnum: 20
					},
					{
						userpic: "../../../static/topicpic/1.jpeg",
						username: "昵称",
						sex: 0, // 0 男，1女
						age: '25',
						isguanzhu: false,
						title: "图文",
						type: 1,
						img: true,
						titlepic: "../../../static/datapic/22.jpg",
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
			//上拉加载更多
			loadMore(index) {
				if (this.tablist[index].loadText != '上拉加载更多') {
					return
				}
				this.tablist[index].loadText = "加载中。。。。"
				setTimeout(() => {
					//加载完成
					let obj = {
						userpic: "../../../static/topicpic/4.jpeg",
						username: "昵称",
						sex: 1, // 0 男，1女
						age: '25',
						isguanzhu: false,
						title: "图文",
						type: 1,
						img: true,
						titlepic: "../../../static/datapic/22.jpg",
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
	.user-space-desc {
		border-radius: 10upx 10upx 0 0;
		background: #FFFFFF;
		position: relative;
		z-index: 10;
		margin-top: -55upx;
		width: 100%;
	}

	.user-space-info {
		padding: 0 30upx;
	}

	.user-space-item {
		padding: 20upx 0;
		color: ;
		border-bottom: 1px solid #EEEEEE;
	}

	.user-space-item>view {
		color: #AAAAAA;
	}

	.user-space-item>view:first-child {
		color: #333333;
		font-size: 35upx;
		padding: 15upx 0;
	}
</style>
