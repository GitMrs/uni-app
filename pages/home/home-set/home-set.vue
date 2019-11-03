<template>
	<view class="home-list">
			<block v-for="(item,index) in list" :key="index">
				<home-list :item="item" :index="index"></home-list>
			</block>
			<button class="user-set-btn" @tap="">退出登陆</button>
		</view>	
</template>

<script>
	import homeList from "../../../components/commom/home-list.vue";
	export default {
		components:{
			homeList
		},
		data() {
			return {
				list:[
					{name:'账号与安全',clicktype:'navigateto',url:'../user-reset-password/user-reset-password'},
					{name:'邮箱绑定'},
					{name:'资料编辑'},
					{name:'小纸条'},
					{name:'清除缓存'},
					{name:'意见反馈'},
					{name:'关于仿糗百'},
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style>
.home-list {
		padding: 20px;
	}
	.user-set-btn{
		width: 100%;
		margin: 20upx 0;
		background: #FFE933;
		border: 0;
		color: #333333;
	}
</style>
