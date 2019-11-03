<template>
	<view>
		<!-- 聊天列表 -->
		<scroll-view id="scrollView" scroll-y="true" :scroll-top="scrollTop" :scroll-with-animation="true" 
		:style="{height:style.contentHeight + 'px'}">
			<block v-for="(item,index) in list" :key="index">
				<view class="user-chat-item">
					<userChatList :item="item" :index="index" />
				</view>
			</block>
		</scroll-view>
	

		<!-- 输入框 -->
		<userChatBootom @submit="submit" />
	</view>
</template>

<script>
	import userChatBootom from '../../components/user-chart/user-chat-bottom.vue';
	import userChatList from '../../components/user-chart/user-chart-list.vue';
	export default {
		components: {
			userChatBootom,
			userChatList
		},
		data() {
			return {
				text: "",
				scrollTop: 0,
				style: {
					contentHeight: 0, //指定滚动的外层高度
					itemH:0 //所有节点的总高度
				},
				list: [{
						isme: false,
						userpic: "../../static/topicpic/1.jpeg",
						type: "text",
						data: "好友",
						time: "165278000"
					},
					{
						isme: true,
						userpic: "../../static/topicpic/2.jpeg",
						type: "image",
						data: "../../static/demo1.jpg",
						time: "165278000"
					}
				]
			}
		},
		onNavigationBarButtonTap(e) {
			if (e.index === 0) {
				uni.navigateBack({
					delta: 1
				})
			}
		},
		onLoad() {
			this.initData()
		},
		methods: {
			//初始化参数
			initData() {
				try {
					const res = uni.getSystemInfoSync();
					this.style.contentHeight = res.windowHeight - uni.upx2px(120);
					console.log(this.style.contentHeight)
				} catch (e) {
					//TODO handle the exception
				}
			},
			pageBottom(){
				// 获取页面的DOM节点
				let q = uni.createSelectorQuery();
				// 获取指定节点
				q.select("#scrollView").boundingClientRect();
				q.selectAll(".user-chat-item").boundingClientRect();
				//得到想要的DOM信息以数组形式获取
				q.exec((res) => {
					// console.log(JSON.stringify(res))
					res[1].forEach((ret) => {
						this.style.itemH += ret.height
					})
					//滚动区域高度大于滚动外层高度
					// console.log(this.style.itemH ,this.style.contentHeight)
					if(this.style.itemH > this.style.contentHeight){
						this.scrollTop = this.style.itemH;
					}
				})
			},
			//获取聊天数据
			getData() {
				let data = []
				for (let i = 0; i < data.length; i++) {
					data[i].isTime = "11:49"
				}
				this.list = data
			},
			submit(data) {
				let res = {
					isme: true,
					userpic: "../../static/topicpic/2.jpeg",
					type: "text",
					data: data,
					time: "165278000"
				}
				this.list.push(res);
				this.pageBottom()
			}
		}
	}
</script>

<style>

</style>
