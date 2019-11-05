<template>
	<view class="commom-list content u-f animated fadeInLeft">
		<view class="commom-list-l">
			<image :src="item.userpic" mode="widthFix" lazy-load></image>
		</view>
		<view class="commom-list-r">
			<view class="u-f-aj u-f-jsb">
				<view class="">
					<view class="u-f-aj">
						<view>{{item.username}}</view>
						<tag-sex-age :sex="item.sex" :age="item.age"></tag-sex-age>
					</view>
					<view class="commom-list-r-time">26天前</view>
				</view>
				<view class="u-f-aj guanzhu">
					<view class="icon iconfont icon-zengjia"></view>关注
				</view>
			</view>
			<view>
				{{item.title}}
			</view>
			<view class="">
				<block v-if="item.type === 0">
					<view class="u-f-aj">
						<view class="">
							{{item.title}}
						</view>
					</view>
				</block>
				<block v-if="item.type === 1">
					<view class="u-f-a" style="flex-direction: column">
						
						<block v-for="(pic,index) in item.morePic" :key="index">
							<image :src="pic" mode="widthFix" @tap="imageDatail(index)"  lazy-load> </image>
						</block>
					</view>
				</block>
				<block v-if="item.type === 2">
					<view class="u-f-aj">
						<image :src="item.titlepic" mode="widthFix" lazy-load> </image>
						<view class="commom-list-play icon iconfont icon-bofang"></view>
						<view class="commom-list-playinfo">
							{{item.video.lonknum}} 次播放 {{item.video.long}}
						</view>
					</view>
				</block>
				<block v-if="item.type === 3">
					<view class="commom-list-share u-f-aj">
						<image :src="item.share.pic" mode="widthFix"  lazy-load></image>
						<view class="">
							{{item.share.title}}
						</view>
					</view>
				</block>
			</view>
			<view class="u-f-aj u-f-jsb">
				<view class="">
					{{item.addree}}
				</view>
				<view class="u-f-aj">
					<view class="u-f-aj">
						<view class="icon iconfont icon-fenxiang"></view>{{item.sharenum}}
					</view>
					<view class="u-f-aj">
						<view class="icon iconfont icon-pinglun1"></view>{{item.commentnum}}
					</view>
					<view class="u-f-aj">
						<view class="icon iconfont icon-dianzan1"></view>{{item.commentnum}}
					</view>
				</view>
			</view>
		</view>
	</view>

</template>

<script>
	import TagSexAge from '../commom/tag-sex-age.vue';
	export default {
		props: {
			index: {
				type: Number
			},
			item: {
				type: Object
			}
		},
		components: {
			TagSexAge
		},
		data() {
			return {

			};
		},
		methods:{
			imageDatail(index){
				uni.previewImage({
					urls:this.item.morePic,
					current:index
				})
			}
		}
	}
</script>

<style scoped>
	@import url("../../common/list.css");

	.commom-list-r .commom-list-r-time {
		color: #ccc;
		font-size: 22upx !important;
		/* margin-top: -10px; */
		/* float: left;
	margin-top: -10px; */
	}
	.commom-list-r image{
		width: 100%;
		margin-bottom: 20upx;
	}
	.guanzhu {
		background: #EEEEEE;
		font-size: 26upx;
		line-height: 26px;
		padding: 0upx 5upx;
		border-radius: 10upx;
	}
</style>
