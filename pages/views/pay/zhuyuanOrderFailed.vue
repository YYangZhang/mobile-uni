<template>
	<view>
		<view class="none" v-if="orderSuccessed">
			<view class="iconfont icon404"></view>
			<view class="div1">
				预缴失败!
			</view>
			<view class="none-text1">
				请您稍后再试~
			</view>
		</view>
		
		<view class="none" v-if="!orderSuccessed">
			<view class="iconfont icon404"></view>
			<view class="none-text">由于系统异常，交易失败。</view>
			<view class="none-text" style="margin-top: 10px;">请您携带就诊卡前往医院窗口办理退费</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				orderSuccessed:false
			}
		},
		methods: {

		}
	}
</script>

<style scoped>
	.div1 {
		font-family: '微软雅黑', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 18px;
		margin-top: 20px;
		color: #333333;
	}
	.none-text1{
		font-size: 14px;
		margin-top: 10px;
	}
</style>
