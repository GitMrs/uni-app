<template>
	<view class="user-chat-bottom u-f-aj">
		<input type="text" v-model="text" placeholder="文明发言" />
		<view class="icon iconfont icon-fabu" @tap="submit"></view>
	</view>
</template>

<script>
	export default {
		data(){
			return {
				text:""
			}
		},
		methods:{
			submit(){
				this.$emit("submit",this.text)
				this.text = "";
			}
		}
	}
</script>

<style>
	.user-chat-bottom{
		position: fixed;
		bottom: 0;
		left: 0;
		right: 0;
		height: 120upx;
		width: 100%;
		padding: 0 20upx;
		background-color: #FFFFFF;
		border-top: 1px solid #EEEEEE;
	}
	.user-chat-bottom>input{
		flex: 1;
		flex-shrink: 0;
		background: #F7F7F7;
		margin-right: 20upx;
		padding-left: 3upx;
		height: 80upx;
		border-radius: 10upx;
	}
	.user-chat-bottom>view{
		width: 60px;
		color: #000000;
		font-size: 60upx;
	}
</style>
