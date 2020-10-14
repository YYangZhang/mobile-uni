<template>
	<view>
		<view class="user">
			<view class="userInfo">
				<view class="userIcon"><image class="userimg" src="../../static/img/2.jpg"></image></view>
				<view class="userName">
					<text>{{ userName }}</text>
				</view>
			</view>
		</view>

		<view class="lists">
			<uni-list>
				<uni-list-item  v-for="(list,i) in  lists" :title="list.title" :thumb="list.img" thumb-size="sm" :clickable="true" @click="gotoMore(list.url,list.title)" :key="i"></uni-list-item>
			</uni-list>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			userName: '甄子丹',
			lists:[
				{
					title:'我的就诊人',
					img:'/static/img/jiuzhen.png',
					url:'../views/patient/defaultPatient'
				},
				{
					title:'我的预约挂号',
					img:'/static/img/yuyue.png',
					url:'../views/mypages/myOrders'
				},
				{
					title:'门诊缴费记录',
					img:'/static/img/menzhen.png',
					url:'../views/mypages/myMenzhenList'
				},
				{
					title:'住院缴费记录',
					img:'/static/img/zhuyuan.png',
					url:'../info/test'
				},
			],
		};
	},
	methods: {
		gotoMore(url,msg) {
			uni.navigateTo({
				// url: "../info/test?params=" + msg,
				url:url + '?params=' + msg
			})
		},
	}
};
</script>

<style scoped>
.user {
	height: 170px;
	position: relative;
	background-color: #268efc;
}
.userInfo {
	position: absolute;
	left: 50%;
	top: 50%;
	transform: translate(-50%, -50%);
	text-align: center;
}
.userIcon {
	width: 65px;
	height: 65px;
	border-radius: 50%;
	border: #ffffff 2px solid;
	overflow: hidden;
}
.userimg {
	width: 100%;
	height: 100%;
}
.userName {
	padding-top: 10px;
	color: #ffffff;
	font-family: 微软雅黑, sans-serif;
	font-weight: 400;
	font-style: normal;
	font-size: 16px;
}
.lists {
	margin-top: 10px;
}
</style>
