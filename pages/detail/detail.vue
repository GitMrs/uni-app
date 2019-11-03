<template>
	<view>
		<!-- 内容 -->
		<detail-info :item="item"></detail-info>
		<!-- 评论 -->
		<view class="u-comment-title">最新评论</view>
		<view class="uni-padding-wrap u-comment">
			<block v-for="(item,index) in content.list" :key="index">
				<comment-list :item="item" :index="index"></comment-list>
			</block>
		</view>
		<!-- 回复评论 -->
		<view style="height: 120upx;">
		</view>
		<user-chat-bootom @submit="submit"></user-chat-bootom>
		<!-- 分享 -->
		<ShareModal :show="shareshow" @closeShare="togle" />
	</view>
</template>

<script>
	import DetailInfo from '../../components/detail/detail-info.vue'
	import commentList from "../../components/detail/comment-list.vue";
	import userChatBootom from "../../components/user-chart/user-chat-bottom.vue";
	import ShareModal from "../../components/commom/share.vue";
	export default {
		components: {
			DetailInfo,
			commentList,
			userChatBootom,
			ShareModal
		},
		data() {
			return {
				shareshow:false,
				content: {
					count: 20,
					list: [{
							fid: 0, //0 一级， 1为二级
							userpic: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/uni@2x.png',
							username: '小猫咪',
							time: '11:34',
							data: '支持国产，支持DCloud!',
						},
						{
							fid: 1,
							userpic: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/uni@2x.png',
							username: '小猫咪',
							time: '11:34',
							data: '支持国产，支持DCloud!',
						},
						{
							fid: 1,
							userpic: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/uni@2x.png',
							username: '小猫咪',
							time: '11:34',
							data: '支持国产，支持DCloud!',
						},
						{
							fid: 0,
							userpic: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/uni@2x.png',
							username: '小猫咪',
							time: '11:34',
							data: '支持国产，支持DCloud!',
						}
					]
				},
				item: {
					userpic: "../../static/topicpic/4.jpeg",
					username: "昵称",
					sex: 0, // 0 男，1女
					age: '25',
					isguanzhu: false,
					title: "图文",
					type: 1, //0 为文字，1 为图文，2 为视频 3，分享
					img: true,
					morePic: ["../../static/datapic/22.jpg"],
					video: false,
					share: false,
					addree: "	深圳 龙岗",
					sharenum: 20,
					commentnum: 30,
					goodnum: 20
				}
			}
		},
		onLoad(e) {
			console.log(1)
			this.initData(JSON.parse(e.detailData));
		},
		//监听右边按钮事件
		onNavigationBarButtonTap(e) {
			e.index === 0 && this.togle()
		},
		methods: {
			initData(obj){
				uni.setNavigationBarTitle({
					title:obj.title
				})
			},
			//打开分享框
			togle(){
				this.shareshow = !this.shareshow;
			},
			//发表评论
			submit(data) {
				let obj = {
						fid: 1,
						userpic: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/uni@2x.png',
						username: '小猫咪',
						time: '11:34',
						data: data,
					}
				this.content.list.push(obj)
			}
		}
	}
</script>

<style>
	.u-comment-title {
		padding: 20upx;
		font-size: 33upx;
		color: #000000;
		font-weight: bold;
	}
</style>
