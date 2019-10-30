<template>
	<view>
		<!-- 自定义导航栏 -->
		<uni-nav-bar :statusBar="true" rightText="发布" left-icon="arrowleft" @click-right="submit" @click-left="back">
			<view class="u-f-aj" style="width: 100%;" @click="changelook">
				{{lookMessage}}
				<view class="icon iconfont icon-xialazhankai"></view>
			</view>
		</uni-nav-bar>
		<!-- 多行输入框 -->
		<view class="uni-textarea">
			<textarea v-model="text" placeholder="说一句话吧～" />
		</view>
			<!-- 上传多图 -->
		<LoadImages @upload="upload" />
			
	</view>
</template>

<script>
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue";
	import LoadImages from '../../components/upload-images.vue';
	let itemList = ["所有人可见","仅自己可见"]
	export default {
		components:{
			uniNavBar,
			LoadImages
		},
		data() {
			return {
				lookMessage:itemList[0],
				text:"",
				imageList:[]
			}
		},
		methods: {
			// 返回
			back(){
				uni.navigateBack({
					delta:1
				})
			},
			// 发布
			submit(){
				
			},
			// 隐私
			changelook(){
				uni.showActionSheet({
					itemList:itemList,
					success:(e)=>{
						this.lookMessage = itemList[e.tapIndex]
						
					},
					fail:()=>{
						
					}
				})
			},
			upload(imageList){
				this.imageList = imageList
			}
		}
	}
</script>

<style>
.uni-textarea{
	border: 1px solid #ccc;
}
</style>
