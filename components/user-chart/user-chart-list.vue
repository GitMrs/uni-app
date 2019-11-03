<template>
	<view>
		<view class="user-chart-time u-f-aj">11:30</view>
		<view class="user-chat-list u-f" :class="{'user-chat-me':item.isme}">
			<image v-if="!item.isme" :src="item.userpic" mode="widthFix" lazy-load></image>
			<view class="user-chat-list-body">
				<text v-if="item.type === 'text'">{{item.data}}</text>
				<image v-if="item.type === 'image'" :src="item.data" mode="widthFix" lazy-load></image>
			</view>
			<image v-if="item.isme" :src="item.userpic" mode="widthFix" lazy-load></image>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			item:Object,
			index:Number
		}
	}
</script>

<style scoped>
	.user-chat-item-wrap{
		
	}
	.user-chart-time {
		padding: 10upx;
		color: #F4F4F4;
	}
	
	.user-chat-list {
		padding: 20upx;
		
	}
	
	.user-chat-list>image {
		width: 100upx;
		height: 100upx;
		border-radius: 100%;
		flex-shrink: 0;
		margin-right: 20upx;
	}
	
	.user-chat-list-body {
		position: relative;
		background: #F4F4F4;
		padding: 25upx;
		margin-left: 20upxs;
		border-radius: 20upx;
		margin-right: 100upx;
	}
	
	.user-chat-list-body:after {
		position: absolute;
		content: "";
		left: -16px;
		top: 15upx;
		width: 0upx;
		height: 0;
		border: 16upx solid #F4F4F4;
		border-color: transparent #F4F4F4 transparent transparent;
	}
	
	.user-chat-list-body>image {
		max-width: 150upx;
		max-height: 200upx;
	}
	
	.user-chat-me {
		justify-content: flex-end;
	}
	
	.user-chat-me .user-chat-list-body {
		margin-right: 20upx;
		margin-left: 100upx;
	}
	
	.user-chat-me .user-chat-list-body:after {
		left: auto;
		right: -30upx;
		border-color: transparent transparent transparent #F4F4F4;
	}
</style>
