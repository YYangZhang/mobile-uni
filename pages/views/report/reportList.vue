<template>
	<view>
		<view class="parent" v-if="showreport">
			<view class="reports" v-for="(report,index) in reports" :key="index">
				<view class="itemtop flex">
					<view class="rptlsp1">检查报告{{index + 1}}</view>
					<view class="rptlsp2">已出报告</view>
				</view>
				<view class="itembot" @click="gotoDetail(report.id)">
					<uni-icons type="arrowright" class="arrowright" size="18" color="#268efd"></uni-icons>
					<view class="botinfo flex">
						<view class="rptlsp3">名称</view>
						<view class="rptlsp4">{{report.name}}</view>
					</view>
					<view class="botinfo flex">
						<view class="rptlsp3">送检日期</view>
						<view class="rptlsp4">{{report.date}}</view>
					</view>
				</view>
			</view>
			<view style="margin-top: 30px;text-align: center;font-size: 30rpx;">只有这么多了</view>
		</view>
		<view class="noreport" v-if="!showreport">
			<view class="iconfont iconkong"></view>
			<view class="noreport-text">
				暂无报告查询
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showreport:true,
				reports: [{
						name: '抗体测试',
						id: '1',
						date: '2020-09-20'
					},
					{
						name: '抗凝血',
						id: '2',
						date: '2020-09-20'
					},
					{
						name: '药检',
						id: '3',
						date: '2020-09-20'
					},
					{
						name: '尿检',
						id: '4',
						date: '2020-09-20'
					},
					{
						name: '心律检查',
						id: '5',
						date: '2020-09-20'
					},
					{
						name: '抗体测试',
						id: '6',
						date: '2020-09-20'
					},
					{
						name: '抗体测试',
						id: '7',
						date: '2020-09-20'
					},
					{
						name: '抗体测试',
						id: '8',
						date: '2020-09-20'
					},
					{
						name: '抗体测试',
						id: '9',
						date: '2020-09-20'
					},
					{
						name: '抗体测试',
						id: '10',
						date: '2020-09-20'
					},
					{
						name: '抗体测试',
						id: '11',
						date: '2020-09-20'
					},
					{
						name: '抗体测试',
						id: '12',
						date: '2020-09-20'
					}
				]
			}
		},
		methods: {
			gotoDetail(msg) {
				uni.navigateTo({
					url: "../report/reportDetail"
				})
			}
		}
	}
</script>

<style scoped>
	.parent {
		padding: 0 10px 10px 10px;
		position: relative;
	}

	.reports {
		margin-top: 10px;
		width: 100%;
		background-color: #FFFFFF;
		border-radius: 8px;
		padding: 14px 0 20px 0;
	}

	.itemtop {
		flex-direction: row;
		flex-wrap: nowrap;
		justify-content: space-between;
		align-items: center;
	}

	.rptlsp1 {
		padding: 2px 14px;
		background-color: #268efd;
		color: #FFFFFF;
		border-radius: 0 10px 10px 0;
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 13px;
	}

	.rptlsp2 {
		padding-right: 14px;
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 12px;
		color: #999999;
	}

	.itembot {
		position: relative;
		padding-left: 24px;
		padding-right: 30px;
	}

	.botinfo {
		flex-direction: row;
		flex-wrap: nowrap;
		align-items: center;
		padding-top: 16px;
	}

	.rptlsp3 {
		width: 80px;
		font-size: 13px;
		color: #999999;
	}

	.rptlsp4 {
		width: calc(100% - 80px);
		font-size: 13px;
		color: #333333;
	}

	.arrowright {
		position: absolute;
		top: 60%;
		transform: translateY(-50%);
		right: 10px;
	}

	.noreport {
		width: 100%;
		margin: 0 auto; 
		text-align: center;
		position: absolute;
		top: 30%;
		transform: translateY(-50%);
	}
	
	.iconkong{
		font-size: 100px;
		color: #999999;
	}
	.noreport-text {
		font-family: '微软雅黑', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 15px;
		color: #333333;
		margin-top: 20px;
	}
</style>
