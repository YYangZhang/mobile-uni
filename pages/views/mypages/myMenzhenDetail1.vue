<template>
	<view style="padding: 0 10px 10px 10px;">
		<view class="div1">
			<view class="div2 flex">
				<view class="div3 blue">{{ detailName }}</view>
				<view class="div4">￥{{ total }}</view>
			</view>
			<view class="div5 txtright">{{ status }}</view>
		</view>
		<view style="height: 10px;"></view>
		<view class="div6">
			<view class="circle1"></view>
			<view class="div7 flex">
				<view class="div8 txtleft blue">药品名称</view>
				<view class="div9 txtcenter blue">规格数量</view>
				<view class="div10 txtright blue">金额</view>
			</view>
			<view class="div11" v-for="(item, index) in list" :key="index">
				<view class="div12">{{ item.name }}</view>
				<view class="div16 flex">
					<view class="div13 txtleft">￥{{ item.price }}</view>
					<view class="div14 txtcenter">×{{ item.nums }}</view>
					<view class="div15 txtright">￥{{ item.price * item.nums }}</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			detailName: '药费',
			total: '200.00',
			status: '已支付',
			list: [
				{
					name: '急支糖浆',
					price: '50.00',
					nums: '2'
				},
				{
					name: '急支糖浆',
					price: '50.00',
					nums: '2'
				},
				{
					name: '急支糖浆',
					price: '50.00',
					nums: '2'
				},
				{
					name: '急支糖浆',
					price: '50.00',
					nums: '2'
				},
				{
					name: '急支糖浆',
					price: '50.00',
					nums: '2'
				},
				{
					name: '急支糖浆',
					price: '50.00',
					nums: '2'
				}
			]
		};
	},
	methods: {}
};
</script>

<style scoped>
page {
	font-family: 'Arial Normal', 'Arial', sans-serif;
	font-weight: 400;
}
.div1 {
	padding: 14px 10px 10px;
	background-color: #ffffff;
	border-radius: 0 0 10px 6px;
}
.div2 {
	flex-direction: row;
	flex-wrap: nowrap;
	justify-content: space-between;
	align-items: center;
	padding-bottom: 10px;
}
.div3 {
	font-size: 16px;
}
.div4 {
	font-size: 14px;
	color: #fd6d52;
}
.div5 {
	color: #999999;
	padding-bottom: 4px;
}
.div6 {
	background-color: #ffffff;
	border: #ffffff 1px double;
	position: relative;
	padding: 10px 10px 20px 10px;
	margin-bottom: 30px;
}
.div7 {
	padding: 10px 0;
	border-bottom: #e8e8e8 1px solid;
	flex-direction: row;
	flex-wrap: nowrap;
	align-items: flex-end;
}
.div16 {
	padding: 4px 0 10px;
	flex-direction: row;
	flex-wrap: nowrap;
	align-items: flex-end;
}
.div11:not(:last-child) {
	border-bottom: #e8e8e8 1px solid;
}
.div8,
.div9,
.div10 {
	font-size: 13px;
}
.div12 {
	padding-top: 10px;
}
.circle1 {
	position: absolute;
	z-index: 5;
	bottom: -6px;
	left: 0;
	transform-origin: center left;
	transform: rotate(0deg);
	width: 100%;
	height: 10px;
	background-image: radial-gradient(circle, #f7f7f7, #f7f7f7 4px, transparent 0px, transparent 2px, transparent 22px, transparent);
	background-size: 10px 10px;
	background-repeat: repeat-x;
}

.div8,
.div9,
.div10,
.div13,
.div14,
.div15 {
	width: 33.33%;
}
.div13,
.div14 {
	font-size: 13px !important;
	color: #9a9a9a;
}
.div12,
.div15 {
	font-size: 14px !important;
	color: #434343;
}
</style>
A
