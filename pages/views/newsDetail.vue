<template>
	<view class="news">
		<view class="news-title">
			<text class="newDsp1 block">{{title}}</text>
			<text class="newDsp2">{{time}}</text>
		</view>
		<view class="news-content">
			<rich-text :nodes="strings"></rich-text>
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
	.news {
		background-color: #FFFFFF;
		padding: 0 10px;
	}

	.news-title {
		padding: 10px;
		border-bottom: #e6e6e6 1px solid;
	}

	.newDsp1 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		color: #333333;
		font-size: 15px;
		padding-bottom: 6px;
	}

	.newDsp2 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 13px;
		letter-spacing: normal;
		color: #999999;
	}

	.news-content {
		padding: 10px;
	}
</style>
