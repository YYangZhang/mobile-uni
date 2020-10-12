<template>
	<view class="fullscreen">
		<view class="selectPatient flex">
			<view class="myOrdersdiv1 color666">
				当前就诊人
			</view>
			<view class="myOrdersdiv1 color666">
				{{name}}
				<uni-icons type="arrowright" size="14" style="margin-left: 6px;" color="#cccccc"></uni-icons>
			</view>
		</view>

		<view class="myOrdersbot">
			<view class="card" v-for="(item,index) in 10" :key="index">

			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				name: '张三丰'
			}
		},
		methods: {

		}
	}
</script>

<style>
	page {
		height: 100%;
	}

	.selectPatient {
		padding: 8px 20px;
		background-color: #FFFFFF;
		flex-direction: row;
		flex-wrap: nowrap;
		justify-content: space-between;
		align-items: center;
		height: 34px;
	}

	.myOrdersdiv1 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 13px;
	}

	.myOrdersbot {
		height: calc(100% - 34px);
		border: red 1px solid;
		padding: 10px;
		overflow: auto;
	}

	.card {
		padding: 14px 10px;
		background-color: #FFFFFF;
		height: 100px;
		border-radius: 6px;
		margin-bottom: 12px;
	}
</style>
