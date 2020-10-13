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
						<view class="div4">住院费用信息</view>
					</view>
					<view class="div2">
						<view class="div5 flex">
							<view class="div6">住院号</view>
							<view class="div7">{{zhuyuanNo}}</view>
						</view>
						<view class="div5 flex div8">
							<view class="div6">科室</view>
							<view class="div7">{{keshi}}</view>
						</view>
						<view class="div5 flex">
							<view class="div6">已预缴金额</view>
							<view class="div7">￥{{money}}</view>
						</view>
					</view>
				</view>
			</view>
			<view class="bot"><button type="primary" class="primarybtn" @click="gotoPay">缴纳住院费用</button></view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			shownone: false,
			money:'1000',
			keshi:'骨科',
			zhuyuanNo:'13852254645521'
		};
	},
	methods: {
		gotoPay(){
			console.log('gotopay')
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
	padding: 20px 10px 0 10px;
}
.div5 {
	flex-direction: row;
	flex-wrap: nowrap;
	align-items: center;
	justify-content: space-between;
	padding: 12px 0;
}
.div6 {
	font-family: 'Arial Normal', 'Arial', sans-serif;
	font-weight: 400;
	font-size: 14px;
	color: #999999;
}
.div7 {
	font-family: 微软雅黑, sans-serif;
	font-weight: 400;
	font-size: 14px;
	color: #333333;
}
.div8{
	border-bottom: #E4E4E4 1px solid;
}
.bot {
	height: 60px;
	padding-top: 10px;
}
</style>
