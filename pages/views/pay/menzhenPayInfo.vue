<template>
	<view class="fullscreen">
		<view class="none" v-if="shownone">
			<view class="iconfont iconkong"></view>
			<view class="none-text">
				暂无门诊缴费信息
			</view>
		</view>
		<view v-if="!shownone" style="height: 100%;">
			<view class="top">
				<view class="card">
					<view class="cardtop">
						<view class="card1">
							{{keshi}}
						</view>
						<view class="card2">
							<view class="flex card3">
								<view class="card4">
									医生：
								</view>
								<view class="card5">
									{{docname}}
								</view>
							</view>

							<view class="flex card3">
								<view class="card4">
									挂号时间：
								</view>
								<view class="card5">
									{{time}}
								</view>
							</view>
						</view>
					</view>
					<view class="cardbot">
						<view class="card6 flex" v-for="(pay,index) in paylist" :key="index" @click="showDetails">
							<uni-icons type="arrowright" size="20" color="#cccccc" class="arrowright"></uni-icons>
							<view>
								{{pay.payname}}
							</view>
							<view class="card7">
								￥{{pay.money}}
							</view>
						</view>
					</view>
				</view>
			</view>
			<view class="bot flex">
				<view class="payInfodiv1 flex">
					<text class="payInfosp1">合计<text class="payInfosp2">{{total}}元</text></text>
				</view>
				<view class="payInfodiv2 flex">
					立即支付
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				keshi: '骨科', //科室名称
				docname: '华佗', //医生姓名
				time: '2020-10-20 15:20', // 挂号时间
				total: 0, // 合计金额
				shownone:false,// 判断是否为空页面
				paylist: [{
						payname: '诊断费',
						money: '999'
					},
					{
						payname: '红包',
						money: '200'
					},
					{
						payname: '医药费',
						money: '10086'
					}
				]
			}
		},
		methods: {
			showDetails() {
				console.log('success')
				uni.navigateTo({
					url: '../pay/menzhenPayDetail'
				})
			},
			getTotal() {
				var v = this;
				v.total = 0;
				for (var i = 0; i < v.paylist.length; i++) {
					v.total += Number(v.paylist[i].money);
				}
				console.log(v.total);
			},
			show(){
				var v = this;
				if (v.paylist.length == 0){
					v.shownone = true
					console.log('数组为空')
				}else{
					v.shownone = false;
					console.log('数组不为空')
				}
			}
		},
		onShow() {
			this.getTotal();
			this.show();
		}
	}
</script>

<style scoped>
	page {
		height: 100%;
		background-color: #f6f6f6;
	}

	.fullscreen {
		position: relative;
	}

	.top {
		height: calc(100% - 50px);
		overflow: auto;
		padding: 10px 10px 2px 10px;
	}

	.card {
		margin-top: 10px;
		border-radius: 10px;
		/* height: 200px; */
		background-color: #FFFFFF;
		overflow: hidden;
	}

	.cardtop {
		background-color: #3595fd;
		padding: 10px;
	}

	.card1 {
		padding: 4px 0 10px 0;
		color: #FFFFFF;
		border-bottom: #FFFFFF 1px solid;
		font-family: 'Arial Negreta', 'Arial', sans-serif;
		font-weight: 700;
		font-style: normal;
		font-size: 16px;
	}

	.card2 {
		padding: 10px 0 2px 0;
	}

	.card3 {
		flex-direction: row;
		flex-wrap: nowrap;
		align-items: center;
		padding-top: 8px;
		color: #FFFFFF;
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-size: 14px;
	}

	.card4 {
		width: 86px;
	}

	.card5 {
		width: calc(100% - 86px);
	}

	.cardbot {
		background-color: #FFFFFF;
		padding: 4px 10px 10px 10px;
	}

	.card6 {
		padding: 20px 30px 20px 0;
		flex-direction: row;
		flex-wrap: nowrap;
		justify-content: space-between;
		align-items: center;
		font-size: 15px;
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		color: #333333;
		position: relative;
	}

	.card7 {
		color: #FF0000;
		font-size: 18px;
	}

	.arrowright {
		position: absolute;
		top: 50%;
		transform: translateY(-50%);
		right: 0px;
	}

	.bot {
		height: 50px;
		flex-direction: row;
		flex-wrap: nowrap;

	}


	.payInfodiv1 {
		background-color: #FFFFFF;
		width: 65%;
		height: 100%;
		align-items: center;
		padding-left: 10px;
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
	}

	.payInfodiv2 {
		background-color: #268efd;
		width: 35%;
		height: 100%;
		align-items: center;
		text-align: center;
		justify-content: space-around;
		color: #FFFFFF;
		font-family: 'Arial Negreta', 'Arial', sans-serif;
		font-weight: 700;
		font-style: normal;
		font-size: 16px;
	}

	.payInfosp1 {
		font-size: 13px;
		color: #333333;
	}

	.payInfosp2 {
		font-size: 18px;
		color: #FF0000;
		margin-left: 10px;
	}

	.card6:not(:last-child) {
		border-bottom: 1px dashed #e4e4e4;
	}
</style>
