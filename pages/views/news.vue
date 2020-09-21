<template>
	<view>
		<view class="news" v-for="(news,idx) in newsList" :key="idx" @click="gotoMore(news.url,news.title,news.time)">
			<view class="news-icon">
				<image :src="news.img" class="news-img"></image>
			</view>
			<view class="news-content">
				<view class="news-title">
					<text>{{news.title}}</text>
				</view>
				<view class="news-time">
					<text>{{news.time}}</text>
				</view>
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
						title: "专家：印度自以为把准了中国的脉 所以敢于咄咄逼人",
						time: "2020/09/20 18:15:10",
						url: "../views/newsDetail",
						id: "aaa"
					},
					{
						img: "../../static/img/2.jpg",
						title: "戏剧性一幕发生了 WeChat在美国的命运反转！",
						time: "2020/09/21 07:28:15",
						url: "../views/newsDetail",
						id: "aaa"
					},
					{
						img: "../../static/img/3.jpg",
						title: "很多种子大量依赖国外 卡脖子都卡到我们碗里了？！",
						time: "2020/09/21 07:25:10",
						url: "../views/newsDetail",
						id: "aaa"
					},
					{
						img: "../../static/img/4.jpg",
						title: "这名香港女大学生接二连三干这事，校方下“禁足令”",
						time: "2020/09/21 05:15:10"
					},
					{
						img: "../../static/img/serviceSelected.png",
						title: "拜登称约有2亿人死于新冠 美媒：美国总共才3亿多人",
						time: "2020/09/21 12:20:03",
						url: "../views/newsDetail",
						id: "aaa"
					},
					{
						img: "../../static/img/1.jpg",
						title: "专家：印度自以为把准了中国的脉 所以敢于咄咄逼人",
						time: "2020/09/20 18:15:10"
					},
					{
						img: "../../static/img/2.jpg",
						title: "戏剧性一幕发生了 WeChat在美国的命运反转！",
						time: "2020/09/21 07:28:15",
						url: "../views/newsDetail",
						id: "aaa"
					},
					{
						img: "../../static/img/3.jpg",
						title: "很多种子大量依赖国外 卡脖子都卡到我们碗里了？！",
						time: "2020/09/21 07:25:10",
						url: "../views/newsDetail",
						id: "aaa"
					},
					{
						img: "../../static/img/4.jpg",
						title: "这名香港女大学生接二连三干这事，校方下“禁足令”",
						time: "2020/09/21 05:15:10",
						url: "../views/newsDetail",
						id: "aaa"
					},
					{
						img: "../../static/img/serviceSelected.png",
						title: "拜登称约有2亿人死于新冠 美媒：美国总共才3亿多人",
						time: "2020/09/21 12:20:03",
						url: "../views/newsDetail",
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
		width: 86px;
		height: 86px;
		line-height: 86px;
		overflow: hidden;
	}

	.news-img {
		width: 100%;
		height: 100%;
		object-fit: cover
	}

	.news .news-content {
		padding: 0 0 0 14px;
		width: calc(100% - 86px);
	}

	.news .news-content .news-title {
		height: 54px;
		margin-bottom: 12px;
		overflow: hidden;
		display: -webkit-box;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 3;
		overflow: hidden;
	}

	.news .news-content .news-title text {
		font-family: '微软雅黑 Regular', '微软雅黑', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 14px;
		color: #333333;
	}

	.news .news-content .news-time {
		text-align: right;
		padding-right: 6px;
	}

	.news .news-content .news-time text {
		font-family: '微软雅黑 Regular', '微软雅黑', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 12px;
		color: #999999;
	}
</style>
