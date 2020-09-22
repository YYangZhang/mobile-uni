<template>
	<view class="fullscreen">
		<view class="content">
			<view class="flex-row">
				<view class="flex-left">
					<image :src="item.img" :class="type == '1' ? 'img1':'img2'"></image>
				</view>
				<view class="flex-right">
					<text class="orsp1" v-if="type == '1'">{{item.docName}}</text>
					<text class="orsp4" v-if="type == '2'">{{item.keshiName}}</text>
					<text class="orsp2">{{item.docId}}</text>
					<text class="block orsp3">
						<text v-if="type == '1'">擅长：</text>
						<text v-if="type == '2'">科室特色：</text>{{item.chara}}
					</text>
				</view>
			</view>
			<view class="content1">
				<view class="showtime">
					<text class="orsp5">就诊时间：
						<text class="orsp6">{{day.year}}-{{day.month}}-{{day.date}} 星期{{day.zhou}}</text>
					</text>
					<text class="orsp7">诊查费<text class="orsp8">{{money}}</text>元</text>
				</view>
				<view class="morning">
					<view class="tb-left">
						aaaaa
					</view>
					<view class="tb-right">
						aaaa
					</view>
				</view>
				<view class="afternoon">
					<view class="tb-left">

					</view>
					<view class="tb-right">

					</view>
				</view>
			</view>
		</view>
		<view class="footer">

		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				item: [], //科室或者医师的信息
				type: '', //门诊类型 专家门诊？普通门诊
				toptitle: '', //头部标题
				day: '', //选中的日期
				money: '15.0'
			}
		},
		methods: {
			setTopTitle() {
				uni.setNavigationBarTitle({
					title: this.toptitle
				});
			}
		},
		onLoad: function(params) {
			this.item = JSON.parse(decodeURIComponent(params.item));
			this.type = params.type;
			this.day = JSON.parse(decodeURIComponent(params.day));
			if (this.type == 1) {
				this.toptitle = '专家门诊'

			} else if (this.type == 2) {
				this.toptitle = '普通门诊'

			}
			this.setTopTitle();
		},
	}
</script>

<style scoped>
	page {
		height: 100%;
	}

	.content {
		height: calc(100% - 50px);
	}

	.footer {
		height: 50px;
		background-color: #0099CC;
	}

	.flex-row {
		display: flex;
		flex-direction: row;
		flex-wrap: nowrap;
		padding: 20px;
		background-color: #199ed8;
	}

	.flex-left {
		width: 50px;
		height: 50px;
		border-radius: 25px;
		overflow: hidden;
		border: #FFFFFF 1px solid;
		background-color: #d4e8fe;
		position: relative;
	}

	.flex-left image {
		position: absolute;
		left: 50%;
		top: 50%;
		transform: translate(-50%, -50%);
	}

	.flex-left .img1 {
		width: 100%;
		height: 100%;
	}

	.flex-left .img2 {
		width: 36px;
		height: 36px;
	}

	.flex-right {
		padding-left: 20px;
		width: calc(100% - 50px);
	}

	.orsp1 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 16px;
		color: #FFFFFF;
	}

	.orsp2 {
		display: inline-block;
		padding-left: 10px;
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 12px;
		color: #FFFFFF;
	}

	.orsp3 {
		padding-top: 10px;
		overflow: hidden;
		display: -webkit-box;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 1;
		color: #FFFFFF;
	}

	.orsp4 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 17px;
		color: #FFFFFF;
	}

	.content1 {
		margin-top: 8px;
		background-color: #FFFFFF;
		padding: 10px;
	}

	.showtime {
		padding-bottom: 10px;
		padding-left: 10px;
		border-bottom: 1px #ebebeb dashed;
	}

	.orsp5 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 14px;
		color: #333333;
	}

	.orsp6 {
		color: #258efb;
		font-weight: bold;
	}

	.orsp7 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 13px;
		color: #666666;
		margin-left: 14px;
	}

	.orsp8 {
		color: #cc0000;
	}

	.morning {
		padding: 30px 10px 10px;
		border-bottom: #ebebeb 1px solid;
	}

	.afternoon {
		padding: 10px 10px 30px;
	}

	.morning,
	.afternoon {
		display: flex;
		flex-direction: row;
		flex-wrap: nowrap;
	}

	.tb-left{
		width: 50%;
		text-align: left;
	}

	.tb-right {
		width: 50%;
		text-align: right;
	}
</style>
