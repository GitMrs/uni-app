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
		<view class="w s t">aaa</view>
			<!-- 上传多图 -->
		<LoadImages @upload="upload" />
		<!-- 弹出层 -->
		<uni-popup :show="showPopup" type="center" class="popup_wrap"  @change="changeTogel">
			<view class="u-f-aj" style="margin: 30upx 0 20upx 0;">
				<image src="../../static/common/addinput.png" mode="widthFix" lazy-load></image>
			</view>
			<view>1、涉及黄色，政治，广告及骚扰信息</view>
			<view>2、涉及人身攻击</view>
			<view>3、留联系方式，透露他人隐私</br> 已经核实即将被严禁，情节严重者永久封禁</view>
			<view>
				<button @click="hidePopup">朕知道了</button>
			</view>
		</uni-popup>
	</view>
</template>

<script>
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue";
	import LoadImages from '../../components/upload-images.vue';
	import uniPopup from "../../components/uni-popup/uni-popup.vue";
	let itemList = ["所有人可见","仅自己可见"]
	export default {
		components:{
			uniNavBar,
			LoadImages,
			uniPopup
		},
		data() {
			return {
				isget:false,
				lookMessage:itemList[0],
				text:"",
				imageList:[],
					showPopup: true,
					content:""
			}
		},
		// 监听返回按钮
		onBackPress(){
			if(!this.text && this.imageList.length < 1) {return false}
			if(!this.isget){
				this.baocun()
				return true;
			}
		},
		methods: {
			//保存为草稿
			baocun(){
				uni.showModal({
					content:"是否要保存为草稿?",
					cancelText:"不保存",
					confirmText:"保存",
					success: (res) => {
						if(res.confirm){
							console.log("保存")
						}else{
							console.log("不保存")
						}
						this.isget= true
						uni.navigateBack({
							delta:1
						})
					}
				})
			},
			// 返回
			back(){
				// console.log(this.showPopup)
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
			},
			changeTogel(e){
				this.showPopup = e.show;
			},
			hidePopup(){
				this.showPopup = false;
			}
		}
	}
</script>

<style>
.uni-textarea{
	border: 1px solid #ccc;
}
.popup_wrap{
	width: 80%;
	font-size: 22upx;
	text-align: left;
}
.popup_wrap view{
	width: 100%;
	text-align: left;
	/* align-content: flex-start; */
}
.popup_wrap>view image{
	width: 75%;
}
.popup_wrap view button{
	background: #F0AD4E;
	color: #FFFFFF;
	margin-top: 30upx;
}
</style>
