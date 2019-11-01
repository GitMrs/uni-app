<template>
	<view class="body">
		<!-- 操作菜单 -->
		<PaperLeftPopup :show="show" @hidePopup="hidePopup" @addfriend="addfriend" @clear="clear" />
		<!-- 列表 -->
		<block v-for="(item,index) in paperData.list" :key="index">
			<PaperList :item="item" :index="index" />
		</block>
		<LoadMore :loadText="paperData.loadText" />
	</view>
</template>

<script>
	import PaperList from "../../components/paper/paper-list.vue";
	import LoadMore from "../../components/commom/load-more.vue";
	import PaperLeftPopup from "../../components/paper/paper-left-popup.vue";
	export default {
		components: {
			PaperList,
			LoadMore,
			PaperLeftPopup
		},
		data() {
			return {
				show:false,
				paperData: {
					loadText: "上拉加载更多",
					list: [{
							userpic: "../../static/topicpic/1.jpeg",
							username: "昵称",
							time: "10:21",
							msg: "嘻嘻嘻",
							noreadnum: "0"
						},
						{
							userpic: "../../static/topicpic/2.jpeg",
							username: "兔子",
							time: "10:21",
							msg: "嘻嘻嘻",
							noreadnum: "2333"
						},
						{
							userpic: "../../static/topicpic/3.jpeg",
							username: "大象",
							time: "10:21",
							msg: "嘻嘻嘻",
							noreadnum: 0
						},
						{
							userpic: "../../static/topicpic/3.jpeg",
							username: "兔子",
							time: "10:21",
							msg: "嘻嘻嘻",
							noreadnum: "2333"
						},
						{
							userpic: "../../static/topicpic/6.jpeg",
							username: "大象",
							time: "10:21",
							msg: "嘻嘻嘻",
							noreadnum: 0
						},
						{
							userpic: "../../static/topicpic/3.jpeg",
							username: "兔子",
							time: "10:21",
							msg: "嘻嘻嘻",
							noreadnum: "2333"
						},
						{
							userpic: "../../static/topicpic/6.jpeg",
							username: "大象",
							time: "10:21",
							msg: "嘻嘻嘻",
							noreadnum: 0
						},
						{
							userpic: "../../static/topicpic/6.jpeg",
							username: "大象",
							time: "10:21",
							msg: "嘻嘻嘻",
							noreadnum: 0
						},
						{
							userpic: "../../static/topicpic/6.jpeg",
							username: "大象",
							time: "10:21",
							msg: "嘻嘻嘻",
							noreadnum: 0
						},
						{
							userpic: "../../static/topicpic/6.jpeg",
							username: "大象",
							time: "10:21",
							msg: "嘻嘻嘻",
							noreadnum: 0
						}
					]

				},
			}
		},
		onPullDownRefresh() {
			this.getMsg()
		},
		onReachBottom() {
			this.loadMore()
		},
		onNavigationBarButtonTap(e) {
			if(e.index === 0){ //点击的左边按钮
			uni.navigateTo({
				url:"../user-list/user-list"
			})
				this.hidePopup();
			}else if(e.index === 1) { // 点击的右边菜单
				this.openPopup();
			}
		},
		methods: {
			addfriend(){
				this.hidePopup();
			},
			clear(){
				this.hidePopup();
			},
			hidePopup(){
				this.show = false;
			},
			openPopup(){
				this.show = true;
			},
			getMsg() {
				let data = [{
						userpic: "../../static/topicpic/5.jpeg",
						username: "昵称",
						time: "10:21",
						msg: "嘻嘻嘻",
						noreadnum: "0"
					},
					{
						userpic: "../../static/topicpic/3.jpeg",
						username: "兔子",
						time: "10:21",
						msg: "嘻嘻嘻",
						noreadnum: "2333"
					},
					{
						userpic: "../../static/topicpic/6.jpeg",
						username: "大象",
						time: "10:21",
						msg: "嘻嘻嘻",
						noreadnum: 0
					}
				]
				setTimeout(() => {
					this.paperData.list = data;
					uni.stopPullDownRefresh();
				}, 2000)
			},
			loadMore() {
				if(this.paperData.loadText !== "上拉加载更多") return;
				let data = {
						userpic: "../../static/topicpic/6.jpeg",
						username: "大象",
						time: "10:21",
						msg: "嘻嘻嘻",
						noreadnum: 0
					}
						this.paperData.loadText = "加载中"
					setTimeout(()=>{
						this.paperData.list.push(data);
						this.paperData.loadText = "上拉加载更多"
					},1000)
				}
		},
	}
</script>

<style>

</style>
