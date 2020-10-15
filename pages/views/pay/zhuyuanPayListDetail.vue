<template>
	<view class="fullscreen">
		<view class="card">
			<view class="div1">
				<view class="div2">
					无敌胖胖
				</view>
				<view class="div3 flex">
					<view>
						时间：<text style="margin-left: 6px;">{{time}}</text>
					</view>
					<view>
						<text class="iconfont iconorder" @click="open"></text>
					</view>
				</view>
			</view>
			<view class="div4">
				<view class="none" v-if="shownone">
					<view class="iconfont iconkong"></view>
					<view class="none-text">暂时没有查询到您的住院费用</view>
				</view>
				<view class="div5" v-if="!shownone">
					<view class="div6">
						住院费用信息
					</view>
					<view class="div7 flex">
						<view class="div8">
							合计
						</view>
						<view class="div8" style="color: #FF0000;">
							￥1500.00
						</view>
					</view>
					<view class="div9">
						<view v-for="(item,index) in orderList" :key="index">
							<view class="div10">
								{{item.name}}
							</view>
							<view class="div11 flex">
								<view>
									￥{{item.price}}×{{item.nums}}
								</view>
								<view>
									￥{{item.price * item.nums}}
								</view>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		<uni-calendar ref="calendar" :insert="false" @confirm="confirm" />
	</view>
</template>

<script>
	export default {
		data() {
			return {
				shownone: false,
				time: '',
				orderList: [{
						name: '抽血',
						price: '50',
						nums: '2'
					},
					{
						name: '放血',
						price: '100',
						nums: '2'
					},
					{
						name: 'X光',
						price: '200',
						nums: '1'
					},
					{
						name: '颅内扫描',
						price: '500',
						nums: '1'
					},
					{
						name: '高血压检查',
						price: '50',
						nums: '1'
					},
					{
						name: '高血脂检查',
						price: '50',
						nums: '1'
					},
					{
						name: '高血糖检查',
						price: '50',
						nums: '1'
					}
				]
			}
		},
		methods: {
			open() {
				this.$refs.calendar.open();
			},
			confirm(e) {
				console.log(e);
				this.time = e.fulldate;
			},
			getNowDate() {
				var myDate = new Date();
				var year = myDate.getFullYear();
				var month = myDate.getMonth() + 1;
				if (month > 0 && month < 10) {
					month = '0' + month;
				}
				var day = myDate.getDate();
				if (day > 0 && day < 10) {
					day = '0' + day;
				}
				this.time = year + '-' + month + '-' + day
			}
		},
		onShow() {
			this.getNowDate();
		}
	}
</script>

<style scoped>
	page {
		height: 100%;
	}

	.fullscreen {
		padding: 14px 10px;
	}

	.card {
		height: 100%;
		border-radius: 10px;
		overflow: hidden;
		background-color: #FFFFFF;
	}

	.div1 {
		padding: 14px 10px;
		background-color: #3595fd;
		color: #FFFFFF;
		font-family: '微软雅黑', sans-serif;
		font-style: normal;
		height: 82px;
	}

	.div2 {
		font-weight: 700;
		font-size: 18px;
	}

	.div3 {
		font-weight: 400;
		font-size: 14px;
		padding-top: 8px;
		flex-direction: row;
		flex-wrap: nowrap;
		justify-content: space-between;
		align-items: center;
	}

	.iconorder {
		margin-right: 10px;
		font-size: 20px;
	}

	.div4 {
		height: calc(100% - 82px);
		position: relative;
	}

	.div5 {
		height: 100%;
		padding: 10px;
	}

	.div6 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 12px;
		color: #666666;
	}

	.div7 {
		padding: 10px 0 14px 0;
		border-bottom: 1px solid #f2f2f2;
		flex-direction: row;
		flex-wrap: nowrap;
		align-items: center;
		justify-content: space-between;
	}

	.div8 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 15px;
		color: #333333;
	}

	.div9 {
		height: calc(100% - 62px);
		overflow: auto;
	}

	.div10 {
		padding-top: 10px;
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 14px;
		color: #333333;
	}

	.div11 {
		flex-direction: row;
		flex-wrap: nowrap;
		align-items: center;
		justify-content: space-between;
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-size: 14px;
		color: #999999;
		padding: 6px 0 4px 0;
		border-bottom: 1px solid #f2f2f2;
	}
</style>
