<template>
	<view class="fullscreen">
		<view class="selectPatient flex">
			<view class="myOrdersdiv1 color666">当前就诊人</view>
			<view class="myOrdersdiv1 color666" @click="changeUser">
				{{ name }}
				<uni-icons type="arrowright" size="14" style="margin-left: 6px;" color="#cccccc"></uni-icons>
			</view>
		</view>

		<view class="myOrdersbot">
			<view class="card" v-for="(order, index) in orderList" :key="index">
				<view class="cardtop flex">
					<view class="myordersp1" :class="{ warnred: order.status == '1', blue: order.status == '3' ,color999: order.status == '2' || order.status == '4'}">{{ diffstatus(order.status) }}</view>
					<!-- // 1为待支付 2为已取消 3为待就诊 4为已就诊 -->
					<view class="myordersp2">快捷挂号</view>
				</view>
				<view class="cardbot" @click="gotopages(order.status)">
					<uni-icons type="arrowright" size="20" class="myordersp5" color="#cccccc"></uni-icons>
					<view class="myordersp3 flex">
						<view>预约科室</view>
						<view class="myordersp4 color333">{{ order.keshi }}</view>
					</view>

					<view class="myordersp3 flex">
						<view>门诊类型</view>
						<view class="myordersp4 color333">{{ order.leixing }}</view>
					</view>

					<view class="myordersp3 flex">
						<view>就诊时间</view>
						<view class="myordersp4 color333">{{ order.shijian }}</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			name: '张三丰',
			orderList: [
				{
					status: '3', // 1为待支付 2为已取消 3为待就诊 4为已就诊
					keshi: '呼吸内科',
					leixing: '普通门诊',
					shijian: '2020-10-20 周四 12:00'
				},
				{
					status: '1',
					keshi: '呼吸内科',
					leixing: '普通门诊',
					shijian: '2020-10-20 周四 12:00'
				},
				{
					status: '2',
					keshi: '呼吸内科',
					leixing: '普通门诊',
					shijian: '2020-10-20 周四 12:00'
				},
				{
					status: '3',
					keshi: '呼吸内科',
					leixing: '普通门诊',
					shijian: '2020-10-20 周四 12:00'
				},
				{
					status: '4',
					keshi: '呼吸内科',
					leixing: '普通门诊',
					shijian: '2020-10-20 周四 12:00'
				},
				{
					status: '4',
					keshi: '呼吸内科',
					leixing: '普通门诊',
					shijian: '2020-10-20 周四 12:00'
				},
				{
					status: '4',
					keshi: '呼吸内科',
					leixing: '普通门诊',
					shijian: '2020-10-20 周四 12:00'
				},
				{
					status: '4',
					keshi: '呼吸内科',
					leixing: '普通门诊',
					shijian: '2020-10-20 周四 12:00'
				},
				{
					status: '4',
					keshi: '呼吸内科',
					leixing: '普通门诊',
					shijian: '2020-10-20 周四 12:00'
				},
				{
					status: '4',
					keshi: '呼吸内科',
					leixing: '普通门诊',
					shijian: '2020-10-20 周四 12:00'
				},
				{
					status: '4',
					keshi: '呼吸内科',
					leixing: '普通门诊',
					shijian: '2020-10-20 周四 12:00'
				}
			]
		};
	},
	methods: {
		gotopages(status){
			if(status == '1'){
				// 待支付
				uni.navigateTo({
					url: "../comp/orderSuccess"
				})
			}else if(status == '2'){
				// 已取消
				uni.navigateTo({
					url: "../comp/canceled"
				})
			}else if(status == '3'){
				// 待就诊
				uni.navigateTo({
					url: "../comp/registerSuccess"
				})
			}else if(status == '4'){
				// 已就诊
				uni.navigateTo({
					url: "../comp/finished"
				})
			}else{
				// 其他
				console.log('error');
			}
		},
		changeUser(){
			uni.navigateTo({
				url: '../patient/selectPatient'
			})
		}
	},
	computed: {
		diffstatus(num) {
			return function(num) {
				var number = Number(num)
				switch (number) {
					// 1为待支付 2为已取消 3为待就诊 4为已就诊
					case 1:
						return '待支付';
					case 2:
						return '已取消';
					case 3:
						return '待就诊';
					case 4:
						return '已就诊';
					default:
						return 'error';
				}
			};
		}
	}
};
</script>

<style>
page {
	height: 100%;
}

.selectPatient {
	padding: 8px 20px;
	background-color: #ffffff;
	flex-direction: row;
	flex-wrap: nowrap;
	justify-content: space-between;
	align-items: center;
	height: 34px;
}

.myOrdersdiv1 {
	font-family: 'Arial Normal', 'Arial', sans-serif;
	font-weight: 400;
	font-style: normal;
	font-size: 13px;
}

.myOrdersbot {
	height: calc(100% - 34px);
	padding: 10px;
	overflow: auto;
}

.card {
	padding: 0px 10px;
	background-color: #ffffff;
	border-radius: 6px;
	margin-bottom: 12px;
}

.cardtop {
	flex-direction: row;
	flex-wrap: nowrap;
	justify-content: space-between;
	align-items: center;
	padding: 14px 0;
	border-bottom: #e4e4e4 1px solid;
}

.cardbot {
	padding-bottom: 20px;
	padding-right: 10px;
	position: relative;
}

.myordersp1 {
	font-family: 微软雅黑, sans-serif;
	font-weight: 700;
	font-size: 16px;
}

.myordersp2 {
	padding: 3px 10px;
	background-color: #02c8be;
	color: #ffffff;
	border-radius: 12px;
}

.myordersp3 {
	flex-direction: row;
	flex-wrap: nowrap;
	align-items: center;
	font-family: 微软雅黑, sans-serif;
	font-weight: 400;
	font-size: 14px;
	color: #999999;
	padding-top: 10px;
}

.myordersp4 {
	margin-left: 14px;
}

.myordersp5 {
	position: absolute;
	right: -2px;
	top: 50%;
	transform: translateY(-50%);
}
</style>
