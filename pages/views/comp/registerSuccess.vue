<template>
	<view>
		<view class="finished">
			<view class="content1 contentbottom">
				<text class="iconfont iconchenggong"></text>
				<text class="block finsp1">挂号成功</text>
			</view>
			<view class="content3 contentbottom">
				<view class="flex-row finpadbot">
					<view class="flex-left">
						<text class="finsp3">就诊序号：</text>
					</view>
					<view class="flex-right">
						<text class="finsp3">{{jzidx}}</text>
					</view>
				</view>
				<view class="flex-row finpadbot">
					<view class="flex-left">
						<text class="finsp3">就诊时间：</text>
					</view>
					<view class="flex-right">
						<text class="finsp3">{{jztime}}</text>
					</view>
				</view>
				<view class="flex-row">
					<view class="flex-left">
						<text class="finsp3">就诊地点：</text>
					</view>
					<view class="flex-right">
						<text class="finsp3">{{jzaddress}}</text>
					</view>
				</view>
			</view>
			<view class="content4 contentbottom">
				<view class="flex-row finpadbot2">
					<view class="flex-left">
						<text class="finsp4">科室：</text>
					</view>
					<view class="flex-right">
						<text class="finsp4">{{keshi}}</text>
					</view>
				</view>
				<view class="flex-row">
					<view class="flex-left">
						<text class="finsp4">门诊类型：</text>
					</view>
					<view class="flex-right">
						<text class="finsp4">{{mztype}}</text>
					</view>
				</view>
			</view>


			<view class="content4 contentbottom">
				<view class="flex-row finpadbot2">
					<view class="flex-left">
						<text class="finsp4">挂号费：</text>
					</view>
					<view class="flex-right">
						<text class="finsp4">￥ {{jzpay}}</text>
					</view>
				</view>
				<view class="flex-row">
					<view class="flex-left">
						<text class="finsp4">状态：</text>
					</view>
					<view class="flex-right">
						<text class="finsp4">{{status}}</text>
					</view>
				</view>
			</view>


			<view class="content4">
				<view class="flex-row finpadbot2">
					<view class="flex-left">
						<text class="finsp4">就诊人：</text>
					</view>
					<view class="flex-right">
						<text class="finsp4">{{jzname}}</text>
					</view>
				</view>
				<view class="flex-row">
					<view class="flex-left">
						<text class="finsp4">提交时间：</text>
					</view>
					<view class="flex-right">
						<text class="finsp4">{{subtime}}</text>
					</view>
				</view>
			</view>
		</view>
		<view class="content5">
			<button type="primary" class="primarybtn">返回首页</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				jzidx: "15",
				jztime: "2020/09/21 周二 上午",
				jzaddress: "门诊四楼东",
				keshi: "消化内科",
				mztype: "专家门诊 齐天大圣",
				jzpay: "10",
				status: "待就诊",
				jzname: "张无忌",
				subtime: "2020/09/20 15:10:10"
			}
		},
		methods: {

		}
	}
</script>

<style scoped>
	page {
		padding: 30px 10px;
	}

	.finished {
		background-color: #FFFFFF;
		border-radius: 10px;
		border: #e4e4e9 1px solid;
		padding: 0 4px;
		/* box-shadow: 1px 1px 1px #e4e4e9; */
	}


	.content1,
	.content2,
	.content3,
	.content4{
		padding: 16px 10px;
	}
	.content5{
		padding: 16px 10px 0;
	}

	.content1 {
		position: relative;
		text-align: center;
	}

	.content1 .iconchenggong {
		position: absolute;
		left: 50%;
		transform: translateX(-50%);
		top: -18px;
		font-size: 30px;
		color: #268efc;
	}

	.content1 .finsp1 {
		font-family: "Arial Negreta", Arial, sans-serif;
		font-weight: 700;
		font-style: normal;
		font-size: 20px;
		padding: 10px 0 6px;
		color: #268efc;
	}

	.flex-row {
		display: flex;
		flex-direction: row;
		flex-wrap: nowrap;
		justify-content: space-between;
		align-items: flex-end;
	}

	.flex-left {
		text-align: left;
	}

	.flex-right {
		text-align: right;
	}

	.finsp3 {
		font-family: "Arial Negreta", Arial, sans-serif;
		font-weight: 700;
		font-style: normal;
		font-size: 15px;
		/* line-height: 30px; */
	}

	.finsp4 {
		font-family: "Arial Normal", Arial, sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 14px;
		color: #999999;
	}

	.finpadbot {
		padding-bottom: 18px;
	}

	.finpadbot2 {
		padding-bottom: 6px;
	}
</style>
