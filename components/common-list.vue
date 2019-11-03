<template>
	<view class="commom-list u-f animated fadeInLeft">
		<view class="commom-list-l">
			<image :src="item.userpic" mode="widthFix" lazy-load></image>
		</view>
		<view class="commom-list-r">
			<view class="u-f-aj u-f-jsb">
				<view class="u-f-aj">
					<view>{{item.username}}</view>
					<tag-sex-age :sex="item.sex" :age="item.age"></tag-sex-age>
				</view>
				<view class="u-f-aj">
					<view class="icon iconfont icon-zengjia"></view>关注
				</view>
			</view>
			<view>
			{{item.title}}
			</view>
			<view class="u-f-aj">
				<block v-if="item.type === 0">
					<view class="u-f-aj">
						<view class="">
							{{item.title}}
						</view>
					</view>
				</block>
				<block v-if="item.type === 1">
					 <image :src="item.titlepic" mode="widthFix" lazy-load> </image>
				</block>
				<block v-if="item.type === 2">
					<image :src="item.titlepic" mode="widthFix" lazy-load> </image>
					<view class="commom-list-play icon iconfont icon-bofang"></view>
						<view class="commom-list-playinfo">
							{{item.video.lonknum}} 次播放 {{item.video.long}}
						</view> 
				</block>
				<block v-if="item.type === 3">
					<view class="commom-list-share u-f-aj">
						<image :src="item.share.pic" mode="widthFix" lazy-load></image>
						<view class="">
							{{item.share.title}}
						</view>
					</view>
				</block>
			
				<!-- 图片 -->
				<!-- <image src="../../static/datapic/22.jpg" mode="widthFix" lazy-load> </image> -->
				<!-- 视频 -->
				<!-- 	<view class="commom-list-play icon iconfont icon-bofang"></view>
					<view class="commom-list-playinfo">
						20w 次播放 2:25
					</view> -->
				<!-- 分享 -->
			<!-- 	<view class="commom-list-share u-f-aj">
					<image src="../../static/datapic/1.jpg" mode="widthFix" lazy-load></image>
					<view class="">
						哈哈哈哈哈哈哈哈哈哈哈哈
					</view>
				</view> -->
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
	import TagSexAge from './commom/tag-sex-age.vue';
	export default {
		props:{
			index:{
				type:Number
			},
			item:{
				type:Object
			}
		},
		components:{
			TagSexAge
		},
		data() {
			return {

			};
		}
	}
</script>

<style>
 @import url("../common/list.css");
</style>
