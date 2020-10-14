<template>
	<view class="fullscreen">
		<view class="selectPatient flex">

			<view class="div2">
				就诊人
			</view>
			<view class="div3" @click="changeUser">
				{{name}}
				<uni-icons type="arrowright" size="18" color="#cccccc" class="arrowright"></uni-icons>
			</view>
		</view>
		<view class="div1">
			<view class="none" v-if="shownone" >
				<view class="iconfont iconkong"></view>
				<view class="none-text">暂无缴费记录哦~</view>
			</view>
			<timeline v-if="!shownone">
				<timelineItem v-for="(order,index) in orderLists" :key="index" :leftTime="order.time">
					<view class="card">
						<view class="div4">
							<view class="div5 flex">
								<view class="div6">
									订单号：{{order.orderNo}}
								</view>
								<view class="div7">
									{{order.ordertype}}
								</view>
							</view>
							<view class="div8">
								{{order.ordertype}}
							</view>
						</view>
						<view class="div9">
							<uni-collapse style="position: relative;">
								<text class="sp2">￥{{order.total}}</text>
								<uni-collapse-item title="合计" :showAnimation="true">
									<view class="div11 flex" v-for="(detail,j) in order.details" :key="j">
										<uni-icons type="arrowright" size="18" color="#cccccc" class="arrowright1"></uni-icons>
										<view class="div12">
											{{detail.name}}
										</view>
										<view class="div13">
											￥{{detail.price}}
										</view>
									</view>
								</uni-collapse-item>
							</uni-collapse>
							<view class="div10 txtright">
								<text class="sp1">订单详情</text>
							</view>
						</view>
					</view>
				</timelineItem>
			</timeline>
		</view>
	</view>
</template>

<script>
	import timeline from '../../../components/chenbin-timeline/timeLine.vue'
	import timelineItem from '../../../components/chenbin-timeline/timelineItem.vue'
	export default {
		data() {
			return {
				name: '无敌胖胖',
				shownone: false,
				orderLists: [{
						time: '2018-07-12  09:39:53',
						orderNo: '12345678910',
						status: '已支付',
						ordertype: '微信缴费',
						total: '150',
						details: [{
								name: '抽血',
								price: '50'
							},
							{
								name: '体检',
								price: '50'
							},
							{
								name: '颅内扫描',
								price: '50'
							}
						]
					},
					{
						time: '2018-07-13  20:39:53',
						orderNo: '12345678910',
						status: '已支付',
						ordertype: '微信缴费',
						total: '150',
						details: [{
								name: '抽血',
								price: '50'
							},
							{
								name: '体检',
								price: '50'
							},
							{
								name: '颅内扫描',
								price: '50'
							}
						]
					},
					{
						time: '2018-07-14  00:39:53',
						orderNo: '12345678910',
						status: '已支付',
						ordertype: '微信缴费',
						total: '150',
						details: [{
								name: '抽血',
								price: '50'
							},
							{
								name: '体检',
								price: '50'
							},
							{
								name: '颅内扫描',
								price: '50'
							}
						]
					}
				]
			}
		},
		components: {
			timeline,
			timelineItem
		},
		methods: {
			changeUser() {
				// 选择就诊人
				uni.navigateTo({
					url: '../patient/selectPatient'
				})
			},
		}
	}
</script>

<style scoped>
	page {
		height: 100%;
		background-color: #f0f2f8;
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
	}

	.selectPatient {
		padding: 10px;
		height: 40px;
		background-color: #FFFFFF;
		flex-direction: row;
		flex-wrap: nowrap;
		justify-content: space-between;
		align-content: center;
	}



	.div2 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 15px;
		color: #999999;
	}

	.div3 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 15px;
		color: #333333;
		padding-right: 24px;
		position: relative;
	}

	.arrowright {
		position: absolute;
		right: 0px;
		top: 50%;
		transform: translateY(-50%);
	}

	.arrowright1 {
		position: absolute;
		right: 8px;
		top: 50%;
		transform: translateY(-50%);
	}

	.div1 {
		height: calc(100% - 40px);
		padding: 10px;
		position: relative;
	}

	.card {
		border-radius: 10px;
		background-color: #FFFFFF;
		overflow: hidden;
	}

	.div4 {
		color: #FFFFFF;
		background-color: #3294fd;
		padding: 0 10px;
	}

	.div5 {
		flex-direction: row;
		flex-wrap: nowrap;
		justify-content: space-between;
		align-items: center;
		padding: 20px 0;
	}

	.div6 {
		font-size: 16px;
	}

	.div7 {
		font-size: 14px;
	}

	.div8 {
		padding: 10px 0;
		font-size: 12px;
	}

	.div9 {
		background-color: #FFFFFF;

	}

	.div10 {
		padding: 10px 10px 11px 10px;
		border-top: #f2f2f2 1px solid;
	}

	.sp1 {
		background-color: #02c8be;
		color: #FFFFFF;
		padding: 3px 10px 3px;
		border-radius: 10px;
		font-size: 12px;
	}

	.div9 /deep/ .uni-collapse-cell__title {
		padding: 0 10px;
		color: #999999;
		height: 48px;
	}

	.div9 /deep/ .uni-collapse-cell__title-text {
		font-size: 15px;
	}

	.div9 /deep/ .uni-collapse-cell {
		border: none !important;
	}

	.div9 /deep/ .uni-collapse-cell--open {
		background-color: #FFFFFF;
	}

	.div9 /deep/ .uni-collapse-cell__title:active {
		background-color: #FFFFFF;
	}

	.sp2 {
		position: absolute;
		top: 12px;
		right: 40px;
		font-size: 18px;
		color: #cc3300;
		font-weight: 700;
	}

	.div11 {
		padding: 13px 30px 13px 10px;
		background-color: #f4f8fb;
		flex-direction: row;
		flex-wrap: nowrap;
		justify-content: space-between;
		align-items: center;
		position: relative;
	}

	.div11:not(:last-child) {
		border-bottom: #cccccc 1px dashed;
	}

	.div12 {
		color: #333333;
		font-size: 15px;
	}

	.div13 {
		color: #666666;
		font-size: 18px;
	}
</style>
