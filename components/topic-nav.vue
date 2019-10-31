<template>
		<view class="topic-nav">
			<view class="u-f-aj u-f-jsb">
				<view>热门分类</view>
				<view class="u-f-aj">
					更多 <view class="icon iconfont icon-jinru"></view>
				</view>
			</view>
			<view class="u-f-aj">
				<view v-for="(item,index) in topicNav" :key="index">{{item.name}}</view>
			</view>
		</view>
</template>

<script>
	export default {
		props:{
			topicNav:{
				type:Array
			}
		},
		data() {
			return {
			};
		}
	}
</script>

<style scoped>
.topic-nav{
	padding: 20upx;
	border-bottom: 1px solid #EEEEEE;
	border-top: 1px solid #EEEEEE;
}
.topic-nav>view:first-child{
	margin-bottom: 10upx;
}
.topic-nav>view:first-child view{
	color: #9E9E9E;
}
.topic-nav>view:first-child>view:first-child{
	color: #333333;
	font-size: 32upx;
}
.topic-nav>view:last-child>view{
	flex: 1;
	background-color: #DDDDDD;
	color: #E9E9E9;
	border-radius: 10upx;
	margin: 0 10upx;
	text-align: center;
	
}
</style>
