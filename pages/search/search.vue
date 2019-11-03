<template>
	<view class="body">
		<template v-if="list.length > 0">
			<block v-for="(item,index) in list" :key="index">
				<index-list :item="item" :index="index"></index-list>
			</block>
			<LoadMore :loadText="loadText" />
		</template>
		<template v-else-if="isSearch && list.length < 0">
			<nothing></nothing>
		</template>
	</view>
</template>

<script>
	import IndexList from '../../components/index-list.vue';
	import Nothing from '../../components/commom/nothing.vue';
	import LoadMore from "../../components/commom/load-more.vue"
	export default {
		components: {
			IndexList,
			Nothing,
			LoadMore
		},
		data() {
			return {
				isSearch:false,
				loadText: "上拉加载更多",
				list: [],
				searchValue:''
			}
		},
		//监听原生标题按钮事件
		onNavigationBarButtonTap(e) {
			if (e.index == 0) {
				//返回上级菜单
				uni.navigateBack({
					delta: 1
				})
			}
			console.log(e)
		},
		//	监听输入框输入事件
		onNavigationBarSearchInputChanged(e) {
			// console.log(e.text)
			// this.isSearch = true;
			this.searchValue = e.text;
			e.text && this.getData();
		},
		//监听键盘搜索页面
		onNavigationBarSearchInputConfirmed() {
			// console.log(e.text)
			// this.searchValue = e.text;
			this.searchValue && this.getData();
			this.isSearch = true;
		},
		//下拉加载更多
		onReachBottom() {
			this.loadMore()
		},
		//监听上拉刷新
		onPullDownRefresh() {
			this.getData();
			// uni.stopPullDownRefresh()
		},
		methods: {
			//搜索事件
			getData(value) {
				//数据请求，关键字key
				uni.showLoading();
				let data = [{
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
				
				setTimeout(()=>{
					this.list = data;
					uni.hideLoading();
				},2000)
			},
			//上拉加载更多
			loadMore() {
				if (this.loadText != '上拉加载更多') {
					return
				}
				this.loadText = "加载中。。。。"
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
					this.list.push(obj)
					this.loadText = "上拉加载更多"
				}, 1000)
				// this.loadText = "没有数据了"
			},
		}
	}
</script>

<style>

</style>
