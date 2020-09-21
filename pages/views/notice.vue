<template>
	<view>
		<view class="news" v-for="(news,idx) in newsList" :key="idx" @click="gotoMore(news.url,news.title,news.time)">

			<view class="news-content">
				<view class="news-title">
					<text>{{news.title}}</text>
				</view>
				<view class="news-contain">
					<text>{{news.contain}}</text>
				</view>
				<view class="news-time">
					<text>{{news.time}}</text>
				</view>
			</view>
			<view class="news-icon">
				<image :src="news.img" class="news-img"></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				newsList: [{
						img: "../../static/img/1.jpg",
						title: "仁济南院专家停诊信息",
						contain: "仁济南院专家停诊信息内容",
						time: "2020/09/20 18:15:10",
						url: "../views/noticeDetail",
						id: "aaa"
					},
					{
						img: "../../static/img/2.jpg",
						title: "仁济南院专家停诊信息",
						contain: "仁济南院专家停诊信息内容",
						time: "2020/09/20 18:15:10",
						url: "../views/noticeDetail",
						id: "aaa"
					},
					{
						img: "../../static/img/3.jpg",
						title: "仁济南院专家停诊信息",
						contain: "仁济南院专家停诊信息内容",
						time: "2020/09/20 18:15:10",
						url: "../views/noticeDetail",
						id: "aaa"
					},
					{
						img: "../../static/img/4.jpg",
						title: "仁济南院专家停诊信息",
						contain: "仁济南院专家停诊信息内容",
						time: "2020/09/20 18:15:10",
						url: "../views/noticeDetail",
						id: "aaa"
					},
					{
						img: "../../static/img/1.jpg",
						title: "仁济南院专家停诊信息",
						contain: "仁济南院专家停诊信息内容",
						time: "2020/09/20 18:15:10",
						url: "../views/noticeDetail",
						id: "aaa"
					},
					{
						img: "../../static/img/2.jpg",
						title: "仁济南院专家停诊信息",
						contain: "仁济南院专家停诊信息内容",
						time: "2020/09/20 18:15:10",
						url: "../views/noticeDetail",
						id: "aaa"
					},
					{
						img: "../../static/img/3.jpg",
						title: "仁济南院专家停诊信息",
						contain: "仁济南院专家停诊信息内容",
						time: "2020/09/20 18:15:10",
						url: "../views/noticeDetail",
						id: "aaa"
					},
					{
						img: "../../static/img/4.jpg",
						title: "仁济南院专家停诊信息",
						contain: "仁济南院专家停诊信息内容",
						time: "2020/09/20 18:15:10",
						url: "../views/noticeDetail",
						id: "aaa"
					}
				]
			}
		},
		methods: {
			gotoMore(url, title, time) {

				uni.navigateTo({
					url: url + '?title=' + title + '&time=' + time
				})
			}
		}
	}
</script>

<style scoped>
	page{
		background-color: #FFFFFF;
	}
	.news {
		padding: 10px;
		border-bottom: #d9d9d9 1px solid;
		display: flex;
		flex-direction: row;
		flex-wrap: nowrap;
		background-color: #FFFFFF;
	}

	.news .news-icon {
		width: 144px;
		height: 95px;
		line-height: 86px;
		overflow: hidden;
	}

	.news-img {
		width: 100%;
		height: 100%;
		object-fit: cover
	}

	.news .news-content {
		padding: 0 12px 0 0;
		width: calc(100% - 144px);
	}

	.news .news-content .news-title {
		height: 46px;
		margin-bottom: 6px;
		overflow: hidden;
		display: -webkit-box;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 2;
		overflow: hidden;
	}

	.news .news-content .news-contain {
		height: 20px;
		margin-bottom: 6px;
		overflow: hidden;
		display: -webkit-box;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 1;
		overflow: hidden;
	}

	.news .news-content .news-title text {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 18px;
		color: #333333;
	}

	.news .news-content .news-contain text {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 14px;
		color: #333333;
	}


	.news .news-content .news-time text {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 12px;
		color: #333333;
	}
</style>
