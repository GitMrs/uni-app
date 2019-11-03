<template>
	<view class="user-list-wrap animated fadeInLeft" @tap="openDatai">
		<view class="user-list u-f-aj">
			<image :src="item.userpic" mode="widthFix" lazy-load></image>
			<view class="">
				<view class="">{{item.username}}</view>
				<tag-sex-age :sex="item.sex" :age="item.age"></tag-sex-age>
			</view>
			<view class="icon iconfont" @tap="change" :class="[isguanzhu? 'icon-xuanze-yixuan' : 'icon-zengjia1']"></view>
		</view>
	</view>
</template>

<script>
	import TagSexAge from "./commom/tag-sex-age.vue";
	export default {
		components:{
			TagSexAge
		},
		props:{
			item:Object,
			index:Number
		},
		data() {
			return {
				isguanzhu:this.item.isguanzhu
			};
		},
		methods:{
			change(){
				this.isguanzhu = !this.isguanzhu
			},
			openDatai(){
				uni.navigateTo({
					url:"../../pages/user-chat/user-chat"
				})
			}
		}
	}
</script>

<style scoped>
	.user-list-wrap{
		padding: 20upx;
	}
	.user-list {
		padding: 10px 0;
		border-bottom: 1px solid #ccc;
		width: 100%;
	}

	.user-list image {
		height: 150upx;
		width: 150upx;
		border-radius: 100%;
		margin-right: 20upx;
		flex-shrink: 0;
	}

	.user-list>view:first-of-type {
		flex: 1;
	}

	.user-list>view:last-of-type {
		width: 30upx;
		color: #CCCCCC;
		/* height: ; */
	}
	.icon-zengjia1{
		color: #F78918 !important;
	}
</style>
