<template>
	<view>
		<view class="canceled">
			<view class="content1 contentbottom">
				<text class="iconfont iconchenggong"></text>
				<text class="block calsp1">取消成功</text>
				<text class="block calsp2">您已成功取消{{text1}}，如有疑问，请与客服联系。</text>
			</view>
			<view class="content2 contentbottom">
				<text class="block calsp3">{{text2}}</text>
				<text class="block calsp3">{{text3}}<text class="calsp4">{{text4}}</text></text>
			</view>
			<view class="content3 contentbottom">
				<text class="block calsp5">候诊时间：<text>{{time}}</text></text>
				<text class="block calsp5">就诊地点：<text>{{address}}</text></text>
			</view>
			<view class="content4 contentbottom">
				<text class="calsp6">挂号费：￥{{money}}元</text>
			</view>
			<view class="content5">
				<text class="block calsp5 noline">就诊人：<text>{{name}}</text></text>
				<text class="block calsp5 noline">提交时间：<text>{{subtime}}</text></text>
			</view>
		</view>
		<view class="content6">
			<button type="primary" class="primarybtn" @tap="orderAgain">重新预约</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				text1: "预约",
				text2: "消化内科",
				text3: "专家门诊",
				text4: "孙思邈",
				time: "2020/09/21 周三 上午",
				address: "门诊四楼东",
				money: "10",
				name: "张无忌",
				subtime: "2020/09/20 15:10:25"
			}
		},
		methods: {
			orderAgain(){
				// 重新预约
				console.log('success')
				uni.navigateTo({
					url: '../orderRegister2'
				})
			}
		},
		// onLoad: function(params) {
		// 	if (params == 'order') {
		// 		uni.setNavigationBarTitle({
		// 			title: 'order'
		// 		});
		// 	} else if (params == 'now') {
		// 		uni.setNavigationBarTitle({
		// 			title: 'now'
		// 		});
		// 	}
		// }
	}
</script>

<style scoped>
	page {
		padding: 30px 10px;
	}

	.canceled {
		background-color: #FFFFFF;
		border-radius: 10px;
		border: #e4e4e9 1px solid;
		padding: 0 4px;
		/* box-shadow: 1px 1px 1px #e4e4e9; */
	}

	
	.content1,
	.content2,
	.content3,
	.content4,
	.content5,
	.content6 {
		padding: 16px 10px;
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
		color: #cccccc;
	}

	

	.content1 .calsp1 {
		font-family: "Arial Negreta", Arial, sans-serif;
		font-weight: 700;
		font-style: normal;
		font-size: 20px;
		padding: 10px 0 20px 0;
		color: #000000;
	}

	.content1 .calsp2 {
		font-family: "Arial Normal", Arial, sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 12px;
		color: #666666;
	}

	.content2 .calsp3 {
		font-family: "Arial Negreta", Arial, sans-serif;
		font-weight: 700;
		font-style: normal;
		font-size: 15px;
		color: #000000;
		line-height: 26px;
	}

	.calsp4 {
		margin-left: 10px;
	}

	.calsp5 {
		font-family: "Arial Normal", Arial, sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 12px;
		color: #999999;
		line-height: 22px;
		text-decoration: line-through;
	}

	.content4 {
		text-align: right;
		padding: 16px 12px;
	}

	.calsp6 {
		font-family: "Arial Negreta", Arial, sans-serif;
		font-weight: 700;
		font-style: normal;
		font-size: 15px;
		color: #999999;
	}

	.noline {
		text-decoration: none;
	}
</style>
