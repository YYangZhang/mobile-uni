<template>
	<view class="fullscreen">
		<view class="none" v-if="shownone">
			<view class="iconfont iconkong"></view>
			<view class="none-text">暂无住院费用信息</view>
		</view>
		<view style="height: 100%;" v-if="!shownone">
			<view class="top">
				<view class="card">
					<view class="div1">
						<view class="div3">无敌胖胖</view>
						<view class="div4">住院号：<text style="margin-left: 10px;">12525225251</text></view>
					</view>
					<view class="div2">
						<view class="div5">
							充值金额
						</view>
						<view class="div6 flex">
							<view class="div7">
								自定义
							</view>
							<input placeholder="请输入充值金额" type="number" class="div8" v-model="money" />
						</view>
						<view class="div9 flex">
							<view class="div10" v-for="(item,index) in moneyList" :key="index">
								<view class="div11 flex" @click="addClass(index,item)" :class="{selected: index == active && money == item}">
									{{item}}
								</view>
							</view>
						</view>
					</view>
				</view>
			</view>
			<view class="bot"><button type="primary" class="primarybtn" @click="gotoPay">去支付</button></view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				money: '1000',
				zhuyuanNo: '13852254645521',
				moneyList: ['500', '1000', '3000', '5000', '10000'],
				money: '',
				active: -1,
				shownone:false
			};
		},
		methods: {
			gotoPay() {
				console.log('gotopay')
				uni.navigateTo({
					url:'../pay/zhuyuanOrderFailed'
				})
			},
			addClass(index, item) {
				var v = this;
				v.active = index;
				v.money = item;
				console.log(v.money);
			}
		}
	};
</script>

<style scoped>
	page {
		height: 100%;
	}

	.top {
		height: calc(100% - 60px);
		overflow: auto;
		padding: 10px;
	}

	.card {
		background-color: #ffffff;
		margin-top: 10px;
		border-radius: 10px;
		overflow: hidden;
	}

	.div1 {
		padding: 20px 10px;
		background-color: #3596fd;
		color: #ffffff;
		font-family: 'Arial Negreta', 'Arial', sans-serif;
	}

	.div3 {
		font-size: 18px;
		font-weight: 700;
	}

	.div4 {
		margin-top: 10px;
		font-size: 14px;
		font-weight: 400;
	}

	.div2 {
		padding: 10px 10px 30px 10px;
	}

	.div5 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 12px;
		color: #666666;
	}

	.div6 {
		flex-direction: row;
		flex-wrap: nowrap;
		align-items: center;
		padding-top: 10px;
	}

	.div7 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 15px;
		width: 80px;
	}

	.div8 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 15px;
		width: calc(100% - 80px);
	}

	.div9 {
		flex-direction: row;
		flex-wrap: wrap;
		padding-top: 10px;
	}

	.div10 {
		width: 33.33%;
		height: 30px;
		margin-top: 10px;
		position: relative;
	}

	.div11 {
		width: 90%;
		height: 100%;
		text-align: center;
		position: absolute;
		left: 50%;
		transform: translateX(-50%);
		color: #999999;
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 13px;
		align-items: center;
		justify-content: space-around;
		border: #999999 1px solid;
		border-radius: 15px;
	}

	.bot {
		height: 60px;
		padding-top: 10px;
	}

	.selected {
		color: #268EFD !important;
		border: #268EFD 1px solid !important;
	}
</style>
