<template>
	<view>
		<uni-nav-bar :statusBar="true" @click-right="add">
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
		
		<block v-for="(item,index) in list" :key="index">
			<commomList :key="index" :item="item"></commomList>
		</block>
		
		
		
		
		
		</view>
</template>

<script>
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue";
	import commomList from '../../components/common-list.vue';
	export default {
		components: {
			uniNavBar,
			commomList
		},
		data() {
			return {
				tabIndex: 0,
				tabBars: [{
						name: "关注"
					},
					{
						name: "话题"
					}
				],
				list: [{
						userpic: "../../static/topicpic/4.jpeg",
						username: "昵称",
						sex: 0, // 0 男，1女
						age: '25',
						isguanzhu: false,
						title: "图文",
						img:true,
						titlepic: "../../static/datapic/22.jpg",
						video: false,
						share: false,
						addree:"	深圳 龙岗",
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
						title: "视频",
						titlepic: "../../static/datapic/22.jpg",
						video: {
							lonknum: '20w',
							long: "2:47"
						},
						share: false,
						addree:"	深圳 龙岗",
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
						video: false,
						share: {
							title: "分享",
							pic: "../../static/datapic/22.jpg"
						},
						addree:"	深圳 龙岗",
						sharenum: 20,
						commentnum: 30,
						goodnum: 20
					}
				]
			}
		},
		methods: {
			changeTab(index) {
				this.tabIndex = index;
			},
			add() {
				uni.navigateTo({
					url: "../add-up/add-up"
				})
			}
		}
	}
</script>

<style>
	.nav-left,
	.nav-right {
		font-size: 40upx;
	}

	.nav-left {
		margin-left: 30upx;
		color: #FF9619;
	}

	.nav-bar-bar {
		width: 100%;
		margin-left: 22upx;
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
