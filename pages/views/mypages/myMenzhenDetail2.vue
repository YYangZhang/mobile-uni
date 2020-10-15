<template>
	<view>
		<view class="div1">
			<view class="div3 flex">
				<view class="div4 blue">
					挂号费
				</view>
				<view class="div5">
					￥100.00
				</view>
			</view>
			<view class="div6">
				已支付
			</view>
			<view class="div7">
				<image src="../../../static/img/txm.jpg"></image>
			</view>
		</view>
		<view style="height: 10px;"></view>
		<view class="div2">
			<view class="div8">
				就诊信息
			</view>
			<view class="div9 flex">
				<view>
					就 诊 人：
				</view>
				<view class="div10 txtright">
					无敌胖胖
				</view>
			</view>
			<view class="div9 flex">
				<view>
					就诊卡号：
				</view>
				<view class="div10 txtright">
					1525856241
				</view>
			</view>
			<view class="div9 flex">
				<view>
					地 点：
				</view>
				<view class="div10 txtright">
					门诊一楼
				</view>
			</view>
			<view class="div9 flex">
				<view>
					窗口：
				</view>
				<view class="div10 txtright">
					3号
				</view>
			</view>
			<view class="div8">
				订单信息
			</view>
			<view class="div9 flex">
				<view>
					订 单 号：
				</view>
				<view class="div10 txtright">
					bc65ab03fd7w4c02aedf
				</view>
			</view>
			<view class="div9 flex">
				<view>
					缴费日期：
				</view>
				<view class="div10 txtright">
					2020-10-18 16:03:06
				</view>
			</view>
			<view class="div9 flex">
				<view>
					支付方式：
				</view>
				<view class="div10 txtright">
					微信支付
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {

		}
	}
</script>

<style scoped>
	page {
		padding: 0 10px;
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
	}

	.div1 {
		background-color: #FFFFFF;
		padding: 10px;
		text-align: right;
		color: #999999;
		font-size: 12px;

		border-radius: 0 0 6px 6px;
	}

	.div3 {
		flex-direction: row;
		flex-wrap: nowrap;
		justify-content: space-between;
		align-items: center;
	}

	.div4 {
		font-size: 15px;
		font-weight: 700;
	}

	.div5 {
		font-size: 14px;
		color: #fd6d52;
	}

	.div6 {
		padding: 6px 0 10px;
		border-bottom: #e8e8e8 1px solid;
	}

	.div7 {
		padding: 20px 0 10px;
	}

	.div7 image {
		width: 100%;
		max-height: 100px;
	}

	.div2 {
		background-color: #FFFFFF;
		padding: 10px;
		border-radius: 6px;
	}

	.div8 {
		padding: 10px 0;
		color: #333333;
		font-size: 14px;
	}

	.div9 {
		flex-direction: row;
		flex-wrap: nowrap;
		justify-content: space-between;
		align-items: center;
		font-size: 14px;
		color: #999999;
		padding: 4px 0 8px 10px;
	}

	.div10 {
		font-size: 14px;
		font-family: 微软雅黑, sans-serif;
		font-weight: 400;
		color: #666666;
	}
</style>
