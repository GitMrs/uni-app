<template>
	<view class="body">
		<view class="home-set-list u-f-aj u-f-jsb">
			<view>头像</view>
			<view class="u-f-aj" @tap="changeImage">
				<image :src="info.userpic" mode="aspectFit" lazy-load></image>
				<view class="icon iconfont icon-bianji1"></view>
			</view>
		</view>
		<view class="home-set-list u-f-aj u-f-jsb">
			<view>昵称</view>
			<view class="u-f-aj">
				<input type="text" style="flex: 1;text-align: right;" v-model="info.username" />
				<view class="icon iconfont icon-bianji1"></view>
			</view>
		</view>
		<view class="home-set-list u-f-aj u-f-jsb">
			<view>性别</view>
			<view class="u-f-aj" @tap="choose('sex')">
				<view class="">{{info.sex}}</view>
				<view class="icon iconfont icon-bianji1"></view>
			</view>
		</view>
		<view class="home-set-list u-f-aj u-f-jsb">
			<view>生日</view>
			<picker mode="date" :value="info.birthday" :start="startDate" :end="endDate" @change="bindDateChange">
				<view class="u-f-aj">
					<view class="">{{info.birthday}}</view>
					<view class="icon iconfont icon-bianji1"></view>
				</view>
			</picker>
		</view>
		<view class="home-set-list u-f-aj u-f-jsb">
			<view>情感</view>
			<view class="u-f-aj" @tap="choose('qg')">
				<view class="">{{info.qg}}</view>
				<view class="icon iconfont icon-bianji1"></view>
			</view>
		</view>
		<view class="home-set-list u-f-aj u-f-jsb">
			<view>职业</view>
			<view class="u-f-aj" @tap="choose('job')">
				<view class="">{{info.job}}</view>
				<view class="icon iconfont icon-bianji1"></view>
			</view>
		</view>
		<view class="home-set-list u-f-aj u-f-jsb">
			<view>家乡</view>
			<view class="u-f-aj" @tap="showMulLinkageThreePicker">
				<view class="">{{info.address}}</view>
				<view class="icon iconfont icon-bianji1"></view>
			</view>
		</view>
		<view><button @tap="submit" :loading="loading" class="user-set-btn">完成</button></view>
		<mpvue-city-picker :themeColor="themeColor" ref="mpvueCityPicker" :pickerValueDefault="cityPickerValueDefault"
		 @onCancel="onCancel" @onConfirm="onConfirm"></mpvue-city-picker>
	</view>
</template>

<script>
	const sex = ["不限", "男", "女"]
	const qg = ["不限", "未婚", "已婚"]
	const job = ["不限", "IT", "教师"]
	
	import mpvueCityPicker from '../../../components/mpvue-citypicker/mpvueCityPicker.vue'
	export default {
		components: {
			mpvueCityPicker
		},
		data() {
			return {
				themeColor: '#007AFF',
				cityPickerValueDefault: [0, 0, 1],
				info: {
					userpic: '../../../static/topicpic/10.jpeg',
					username: '哈哈哈',
					sex: '不限',
					birthday: "2019-03-11",
					qg: '不限',
					job: 'IT',
					address: '广东'
				}
			}
		},
		computed: {
			startDate() {
				return this.getDate('start');
			},
			endDate() {
				return this.getDate('end');
			}
		},
		methods: {
			// 三级联动选择
			showMulLinkageThreePicker() {
				this.$refs.mpvueCityPicker.show()
			},
			onCancel(e) {
				console.log(e)
			},
			onConfirm(e) {
				this.info.address = e.label
			},
			//日期选择
			bindDateChange(e) {
				// console.log(e.target.value)
				this.info.birthday = e.target.value
			},
			changeImage() {
				uni.chooseImage({
					sizeType: "compressed",
					success: (res) => {
						this.info.userpic = res.tempFilePaths
					}
				})
			},
			choose(val) {
				let arr = []
				switch (val) {
					case 'sex':
						arr = sex;
						break;
					case 'qg':
						arr = qg;
						break;
					case 'job':
						arr = job;
						break;
					default:
						break;
				}
				uni.showActionSheet({
					itemList: arr,
					success: (e) => {
						switch (val) {
							case 'sex':
								this.info.sex = sex[e.tapIndex];
								break;
							case 'qg':
								this.info.qg = qg[e.tapIndex];
								break;
							case 'job':
								this.info.job = job[e.tapIndex];
								break;
							default:
								break;
						}
					}
				})
			},
			submit() {},
			getDate(type) {
				const date = new Date();
				let year = date.getFullYear();
				let month = date.getMonth() + 1;
				let day = date.getDate();

				if (type === 'start') {
					year = year - 60;
				} else if (type === 'end') {
					year = year + 2;
				}
				month = month > 9 ? month : '0' + month;;
				day = day > 9 ? day : '0' + day;
				return `${year}-${month}-${day}`;
			}
		},
		onBackPress() {
		  if (this.$refs.mpvuePicker.showPicker) {
		  	this.$refs.mpvuePicker.pickerCancel();
		    return true;
		  }
		  if (this.$refs.mpvueCityPicker.showPicker) {
		  	this.$refs.mpvueCityPicker.pickerCancel();
		    return true;
		  }
		},
		onUnload() {
			if (this.$refs.mpvuePicker.showPicker) {
				this.$refs.mpvuePicker.pickerCancel()
			}
			if (this.$refs.mpvueCityPicker.showPicker) {
				this.$refs.mpvueCityPicker.pickerCancel()
			}
		}
	}
</script>

<style>
	@import url("../../../common/form.css");

	.home-set-list {
		padding: 20upx;
		color: #989898;
		border-bottom: 1px solid #E5E5E5;
	}

	.home-set-list>view {
		font-size: 26upx;
	}

	.home-set-list>view:last-child image {
		height: 100upx;
		width: 100upx;
		border-radius: 100%;
	}

	.home-set-list>view:last-child>view:first-child {
		color: #000000;
	}

	.home-set-list>view:last-child>view:last-child {
		margin-left: 20upx;
	}
</style>
