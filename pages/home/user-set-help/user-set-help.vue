<template>
	<view>
		<uni-collapse accordion="true">
			<uni-collapse-item title="客服什么时候在线" :showAnimation="true" :open="true">
				<view class="content">
					亲爱的仿糗友，客服的工作时间为：周一至周六10:00-12:00,14:00-19:00，非工作时间的自选反馈会自动转为留言，客服上班后悔第一时间回复哦~<br />
					<view style="margin-top: 30upx;">
						PS.紧急问题可以添加官方XXXXXXXXXX进行反馈
					</view>
				</view>
			</uni-collapse-item>
			<uni-collapse-item title="忘记账号/密码/昵称怎么办？" :showAnimation="true">
				<view class="content">亲爱的仿糗友，客服的工作时间为：周一至周六10:00-12:00,14:00-19:00，非工作时间的自选反馈会自动转为留言，客服上班后悔第一时间回复哦~</view>
			</uni-collapse-item>
			<uni-collapse-item title="怎么搜索/查找/关注/取关/用户" :showAnimation="true">
				<view class="content">亲爱的仿糗友，客服的工作时间为：周一至周六10:00-12:00,14:00-19:00，非工作时间的自选反馈会自动转为留言，客服上班后悔第一时间回复哦~</view>
			</uni-collapse-item>
		</uni-collapse>
	</view>
</template>

<script>
	import uniCollapse from '../../../components/uni-collapse/uni-collapse.vue'
	import uniCollapseItem from "../../../components/uni-collapse-item/uni-collapse-item.vue"
	export default {
		components: {
			uniCollapse,
			uniCollapseItem
		},
		data() {
			return {

			}
		},
		methods: {

		}
	}
</script>

<style>
	@import url("../../../common/form.css");

	.content {
		padding: 20upx;
		background: #FFFFFF;
		text-indent: 20upx;
		font-size: 30upx;
		line-height: 60upx;
		color: #C0C0C0;
	}
</style>
