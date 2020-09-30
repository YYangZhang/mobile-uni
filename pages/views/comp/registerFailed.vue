<template>
	<view class="fullscreen">
		<view class="head">
			<view class="failed">
				<text class="iconfont iconcuowu"></text>
				<text class="regfailedsp">挂号失败</text>
			</view>
		</view>
		<view class="foot">
			<button type="default" class="primarybtn">返回首页</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {

		}
	}
</script>

<style scoped>
	page {
		height: 100%;
		background-color: #f0f2f8;
	}

	.head {
		position: relative;
		height: calc(100% - 60px);
	}

	.foot {
		height: 60px;
	}

	.failed {
		position: absolute;
		left: 50%;
		top: 40%;
		transform: translate(-50%, -50%);
		text-align: center;
	}

	.iconcuowu {
		font-size: 80px;
		color: #f04134;
	}

	.regfailedsp {
		display: block;
		padding-top: 40px;
		font-family: "Arial Normal", Arial, sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 18px;
	}

	.primarybtn {
		margin: 0 auto;
		color: #FFFFFF;
	}
</style>
