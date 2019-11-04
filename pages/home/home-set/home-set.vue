<template>
	<view class="home-list">
			<block v-for="(item,index) in list" :key="index">
				<home-list :item="item" :index="index"></home-list>
			</block>
			<button class="user-set-btn">退出登陆</button>
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
					{name:'邮箱绑定',clicktype:'navigateto',url:'../user-set-email/user-set-email'},
					{name:'资料编辑',clicktype:'navigateto',url:'../user-set-info/user-set-info'},
					{name:'小纸条'},
					{name:'清除缓存'},
					{name:'意见反馈',clicktype:'navigateto',url:'../user-set-help/user-set-help'},
					{name:'关于仿糗百',clicktype:'navigateto',url:'../user-set-about/user-set-about'},
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style>
@import url("../../../common/form.css");
.home-list {
		padding: 20px;
	}

</style>
