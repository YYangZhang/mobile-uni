<template>
	<view>
		<view class="notice">
			<text class="notice-title block">{{title}}</text>
			<text class="notice-time">{{time}}</text>
			<view class="contain">
				<rich-text :nodes="strings"></rich-text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: "",
				time: "",
				strings: '<div style="text-align:center;"><img src="https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/uni@2x.png"/></div>'
			}
		},
		methods: {

		},
		onLoad: function(params) {
			this.title = params.title;
			this.time = params.time;
		}
	}
</script>

<style scoped>
	page{
		background-color: #FFFFFF;
	}
	.notice{
		padding: 15px 10px;
	}
	.notice-title {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 18px;
		color: #333333;
		padding-bottom: 8px;
	}

	.notice-time {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 12px;
		color: #333333;
	}
	.contain{
		padding-top: 30px;
	}
</style>
