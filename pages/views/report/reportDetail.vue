<template>
	<view>
		<view class="detailtop">
			<text class="name">血常规</text>
			<view class="rptDdiv2">
				<view class="flex rptDdiv1">
					<view class="rptDsp1">姓名：</view>
					<view class="rptDsp2">张耀扬</view>
					<view class="rptDsp3">性别：</view>
					<view class="rptDsp4">男</view>
				</view>
				<view class="flex rptDdiv1">
					<view class="rptDsp1">年龄：</view>
					<view class="rptDsp2">18</view>
					<view class="rptDsp3">送检日期：</view>
					<view class="rptDsp4">2020-07-22</view>
				</view>
			</view>
		</view>
		<view class="detailbot">
			<view class="bluediv">
				报告结果
				<view class="download">
					<text class="iconfont iconxiazai"></text>
					下载
				</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {};
	},
	methods: {}
};
</script>

<style scoped>
.detailtop {
	background-color: #ffffff;
	padding: 18px 0 30px 0;
}

.name {
	padding: 2px 12px 3px 10px;
	background-color: #12bde8;
	color: #ffffff;
	width: auto;
	display: inline-block;
	border-radius: 0 11px 11px 0;
	font-family: 'Arial Normal', Arial, sans-serif;
	font-weight: 400;
	font-style: normal;
	font-size: 13px;
}

.rptDdiv2 {
	padding: 20px 20px 0 20px;
}

.rptDdiv1 {
	flex-direction: row;
	flex-wrap: nowrap;
	padding-top: 10px;
}

.rptDsp1 {
	width: 50px;
	font-family: 'Arial Normal', 'Arial', sans-serif;
	font-weight: 400;
	font-style: normal;
	font-size: 14px;
	color: #333333;
}

.rptDsp2 {
	width: calc(45% - 50px);
	font-family: 'Arial Normal', 'Arial', sans-serif;
	font-weight: 400;
	font-style: normal;
	font-size: 14px;
	color: #666666;
}

.rptDsp3 {
	width: 80px;
	font-family: 'Arial Normal', 'Arial', sans-serif;
	font-weight: 400;
	font-style: normal;
	font-size: 14px;
	color: #333333;
}

.rptDsp4 {
	width: calc(55% - 80px);
	font-family: 'Arial Normal', 'Arial', sans-serif;
	font-weight: 400;
	font-style: normal;
	font-size: 14px;
	color: #666666;
}

.detailbot {
	padding: 10px;
}

.bluediv {
	height: 40px;
	position: relative;
	text-align: center;
	width: 100%;
	background-color: #258efc;
	border-radius: 4px 4px 0 0;
	line-height: 40px;
	font-family: 'Arial Negreta', 'Arial', sans-serif;
	font-weight: 700;
	font-style: normal;
	font-size: 16px;
	color: #ffffff;
}
.download {
	position: absolute;
	color: #ffffff;
	right: 10px;
	top: 0;
}
.iconxiazai{
	font-size: 22px;
	font-weight: 400;
	line-height: normal;
	position: relative;
	top: 3px;
	margin-right: 4px;
}
</style>
