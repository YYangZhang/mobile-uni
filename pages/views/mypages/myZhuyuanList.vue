<template>
	<view class="fullscreen">
		<uni-search-bar :radius="100" @confirm="search" cancelButton="auto" clearButton="auto" class="searchbtn"></uni-search-bar>
		<view class="div1" v-if="showResult">
			<view class="none" v-if="shownone">
				<view class="iconfont iconkong"></view>
				<view class="none-text">暂无缴费记录哦~</view>
			</view>
			<view class="div2" v-if="!shownone">
				<view class="card">
					<view class="div3">
						{{name}}<text style="margin-left: 10px;font-weight: 400;">{{phone}}</text>
					</view>
					<view class="div4">
						<view class="div5 flex" v-for="(item,index) in lists" :key="index">
							<view>
								<view class="div8">
									{{item.zhuyuanorder}}
								</view>
								<view class="div9">
									{{item.time}}
								</view>
							</view>
							<view class="div7">
								￥{{item.money}}
							</view>
						</view>
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
				showResult:false,
				shownone: false,
				name: '无敌胖胖',
				phone: '17602525252',
				lists: [{
						zhuyuanorder: '住院预交金',
						time: '2020-06-20 17:00:00',
						money: '1700.00'
					},
					{
						zhuyuanorder: '住院预交金',
						time: '2020-06-21 17:00:00',
						money: '1800.00'
					},
					{
						zhuyuanorder: '住院预交金',
						time: '2020-06-25 17:00:00',
						money: '3000.00'
					},
					{
						zhuyuanorder: '住院预交金',
						time: '2020-07-10 17:00:00',
						money: '5000.00'
					},
					{
						zhuyuanorder: '住院预交金',
						time: '2020-07-30 17:00:00',
						money: '10000.00'
					},
					{
						zhuyuanorder: '住院预交金',
						time: '2020-07-30 17:00:00',
						money: '10000.00'
					},
					{
						zhuyuanorder: '住院预交金',
						time: '2020-07-30 17:00:00',
						money: '10000.00'
					},
					{
						zhuyuanorder: '住院预交金',
						time: '2020-07-30 17:00:00',
						money: '10000.00'
					},
					{
						zhuyuanorder: '住院预交金',
						time: '2020-07-30 17:00:00',
						money: '10000.00'
					},
					{
						zhuyuanorder: '住院预交金',
						time: '2020-07-30 17:00:00',
						money: '10000.00'
					},
					{
						zhuyuanorder: '住院预交金',
						time: '2020-07-30 17:00:00',
						money: '10000.00'
					}
				]
			}
		},
		methods: {
			search(e) {
				console.log(e)
				this.showResult = true;
			}
		},
		onShow() {
			this.showResult = false;
		}
	}
</script>

<style scoped>
	page {
		height: 100%;
		font-family: 'Arial Negreta', 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
	}

	.div1 {
		height: calc(100% - 52px);
		position: relative;
		overflow: auto;
	}

	.div2 {
		padding: 10px 10px 20px;
		height: 100%;
	}

	.card {
		height: 100%;
		overflow: hidden;
		border-radius: 10px;
	}

	.div3 {
		font-family: 'Arial Negreta', 'Arial Normal', 'Arial', sans-serif;
		font-weight: 700;
		font-style: normal;
		font-size: 16px;
		color: #FFFFFF;
		background-color: #61a0ef;
		padding: 10px 20px;
		height: 42px;
	}

	.div4 {
		padding: 10px 20px;
		overflow: auto;
		height: calc(100% - 42px);
		background-color: #FFFFFF;
	}

	.div5 {
		flex-direction: row;
		flex-wrap: nowrap;
		align-items: center;
		justify-content: space-between;
	}

	.div5:not(:last-child) {
		border-bottom: #e8e8e8 1px solid;
	}

	.div7 {
		font-size: 17px;
		color: #CC3300;
	}

	.div8 {
		font-size: 14px;
		padding: 10px 0;
	}

	.div9 {
		font-size: 13px;
		color: #666666;
		padding: 4px 0;
	}

	.searchbtn {
		background-color: #f7f7f7;
	}

	.searchbtn /deep/ .uni-searchbar__box {
		background-color: #FFFFFF !important;
	}
</style>
