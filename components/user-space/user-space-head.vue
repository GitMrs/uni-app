<template>
	<view class="user-space-head u-f-aj">
		<image class="bg" src="../../../static/datapic/26.jpg" mode="widthFix" lazy-load></image>
		<view class="user-space-head-info u-f-aj">
			<image src="../../../static/topicpic/11.jpeg" mode="widthFix" lazy-load></image>
			<view class="user-space-margin u-f-aj">xxxx <tag-sex-age :sex="1" :age="15"></tag-sex-age>
			</view>
			<view @tap.stop="changeGuanzhu" class="icon iconfont icon-zengjia user-space-head-btn user-space-margin" :class="{'user-space-head-unbtn':!isguanzhu}">
				{{isguanzhu ? '已关注' : '关注'}}
			</view>
		</view>
	</view>
</template>

<script>
	import TagSexAge from '../commom/tag-sex-age.vue';
	export default {
		components:{
			TagSexAge
		},
		props:{
			item:Object
		},
		data(){
			return {
				isguanzhu:this.item.isguanzhu
			}
		},
		methods: {
			changeGuanzhu() {
				this.isguanzhu = !this.isguanzhu
				console.log(this.isguanzhu)
			}
		}
	}
</script>

<style scoped>
	.user-space-margin {
		margin: 10upx 0;
	}
	
	.user-space-head {
		position: relative;
		height: 500upx;
		overflow: hidden;
	}
	
	.user-space-head>image {
		width: 100%;
	}
	
	.user-space-head-info {
		flex-direction: column;
		position: absolute;
		top: 130upx;
	}
	
	.user-space-head-info>image {
		width: 150upx;
		height: 150upx;
		border-radius: 100%;
	}
	
	.user-space-head-info>view:first-of-type {
		font-size: 40upx;
		color: #FFFFFF;
		text-shadow: 2upx 2upx 10upx #ccc;
		font-weight: bold;
	}
	
	.user-space-head-btn {
		padding: 0 15upx;
		font-size: 22upx;
		background: #FFE933;
		color: #333333;
		border-radius: 10upx;
		border: 1upx solid #FFE933;
	}
	
	.user-space-head-unbtn {
		padding: 0 15upx;
		border: 1upx solid #fff;
		background-color: rgba(0, 0, 0, 0);
		color: #FFFFFF;
	}
	
</style>
