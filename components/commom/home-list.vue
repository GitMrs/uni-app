<template>
	<view class="u-f-aj u-f-jsb home-list-item" hover-class="home-list-hover" @tap="clickEvent">
		<view class="u-f-aj"><view class="icon iconfont" :class="[item.icon ? 'icon-' + item.icon : '']"></view>{{item.name}}</view>
		<view class="icon iconfont icon-jinru"></view>
	</view>
</template>

<script>
	export default {
		props:{
			item:Object,
			index:Number
		},
		methods:{
			clickEvent(){
				switch(this.item.clicktype){
					case 'navigateto' :
						if(this.item.url){ uni.navigateTo({url:this.item.url})}
					break;
					case 'clear':
						this.clear()
					break;
				}
			},
			clear(){
				uni.showModal({
						title:"提示",
						content:"是否要清楚缓存？",
						confirmText:"立即清除",
						success:res => {
							if(res.confirm){
								uni.clearStorage();
								uni.showToast({
									title:"清楚缓存成功"
								})
							}
						}
				})
			}
		}
	}
</script>

<style scoped>
	.home-list-item{
		padding: 20upx;
		/* border-top: 1upx solid #EEEEEE; */
		border-bottom: 1upx solid #EEEEEE;
	}
	.home-list-item>view:first-child{
		color: #333333;
	}
	.home-list-item>view:first-child>view{
		margin-right: 10upx;
	}
	.home-list-item>view:last-child{
		color: #CCCCCC;
	}
	.home-list-hover{
		background: #F4F4F4;
	}
</style>
