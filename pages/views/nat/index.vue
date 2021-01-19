<template>
	<view class="fullscreen">
		<view class="indexContent">
			<view v-for="(item,index) in titleList" :key="index">
				<view class="stepContent">
					<view class="stepIcon">
						<text class="iconfont" :class="item.icon"></text>
					</view>
					<view class="stepCon">
						<view class="title">
							<text>{{item.title}}</text>
						</view>
						<view class="content">
							<text>{{item.con}}</text>
						</view>
					</view>
					<view class="stepBtn">
						<view class="btn">
							<text>{{item.btn}}</text>
						</view>
					</view>
				</view>
				<view class="downarrow" v-if="!(titleList.length == index+1)">
					<text class="iconfont iconxiangxiagengduo arrowicon"></text>
				</view>
			</view>
			<view class="nattips">
				<uni-icons type="info-filled" size="20" color="#007aff" style="margin-right: 8px;"></uni-icons>
				<text> 核酸检测预约步骤：1、填写调查问卷→2、核酸挂号付费→3、核酸化验单付费→4、核酸检测预约→5、查看检测报告；</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				titleList: [{
						icon: 'iconyiyuan1',
						title: '核酸挂号付费',
						con: '核酸检测需要先进行挂号付费',
						btn: '立即挂号',
						url: '',
					},
					{
						icon: 'icon1',
						title: '核酸化验单付费',
						con: '核对核酸化验单并付费',
						btn: '检查付费',
						url: '',
					},
					{
						icon: 'iconyuyue',
						title: '核酸检测预约',
						con: '在线预约核酸检测',
						btn: '核酸预约',
						url: '',
					},
					{
						icon: 'iconbaogaochaxun',
						title: '查看报告',
						con: '检测完成后在线查报告',
						btn: '点击查看',
						url: '',
					}
				]
			}
		},
		methods: {

		}
	}
</script>

<style lang="less" scoped>
	page {
		height: 100%;
		overflow: auto;
		background: linear-gradient(#286efc, #85bffd, #bedcfd);
	}

	.fullscreen {
		padding: 16px 16px 0 16px;
	}

	.indexContent {
		/* border: red 1px solid; */
	}

	.stepContent {
		padding: 20px 10px;
		background-color: #FFFFFF;
		border-radius: 6px;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}

	.stepIcon {
		color: #546186;
		width: 80rpx;
		height: 80rpx;
		margin-right: 40rpx;

		.iconfont {
			font-size: 80rpx;
		}

	}

	.stepCon {
		flex: 1;

		.title {
			font-size: 40rpx;
			font-weight: bold;
			color: #333333;
			padding-bottom: 16rpx;
		}

		.content {
			color: #999999;
			font-size: 28rpx;
		}
	}

	.stepBtn {
		font-size: 12px;
	}

	.btn {
		font-size: 30rpx;
		padding: 4px 18px;
		background-color: #148cf1;
		color: #FFFFFF;
		border-radius: 40rpx;
	}

	.downarrow {
		text-align: center;
	}

	.arrowicon {
		font-size: 40px;
		color: #FFFFFF;
	}

	.nattips {
		padding-top: 30px;
		display: flex;
		font-size: 14px;
		padding-bottom: 16px;
	}
</style>
